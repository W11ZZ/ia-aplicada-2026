
# Transformaciones — Laboratorio Semana 3

Dataset ficticio de solicitudes de acceso (45 filas crudas, 42 tras eliminar duplicados exactos).

## 1\. Transformaciones aplicadas por columna

| Columna original | Qué le hicimos | Técnica | Por qué |
| :---- | :---- | :---- | :---- |
| id | Conservar |  | Solo es llave de fila; no identifica a nadie |
| nombre | Seudonimizar | Código estable `P001…P038` con `BUSCARV` contra una tabla privada (no subida al repositorio) | Identificador directo; la misma persona conserva el mismo código para poder analizar su comportamiento |
| correo | Eliminar | Columna borrada (la versión enmascarada `c***@correo.com` se probó y también se descartó) | Identificador directo; no se necesita para detectar patrones de acceso |
| telefono | Eliminar | Columna borrada | Identificador directo; no aporta al análisis |
| fecha\_acceso | Generalizar | Número de semana del año (`NUM.DE.SEMANA`) | Quita el día exacto pero conserva la frecuencia |
| hora\_entrada | Generalizar | Franja: Madrugada, Mañana, Tarde, Noche | Permite detectar accesos inusuales sin exponer el minuto exacto |
| area | Conservar |  | Necesaria para el análisis; por sí sola no identifica |
| empresa | Generalizar | Agrupar por giro: Constructora, Diseño, Soporte TI (`Sin dato` si estaba vacía) | Identificador indirecto; el nombre de la empresa combinado con área y hora podía señalar a una persona |
| motivo | Conservar |  | Necesaria para el análisis; por sí sola no identifica |

## 2\. Errores introducidos vs. detectados en la limpieza

| Tipo de error | Filas (id) | Introducidos | Detectados/corregidos | Faltaron | Por qué |
| :---- | :---- | :---- | :---- | :---- | :---- |
| Fila duplicada exacta | 1/4, 11/20, 25/35 | 3 | 3 (herramienta Quitar duplicados, sin la columna `id`) | 0 |  |
| Duplicado que solo difiere en mayúsculas | 3 y 8 | 1 par | 0 como duplicado | 1 par | Tras normalizar, el teléfono sigue distinto (5511223344 vs 5566677788), así que no es duplicado exacto; se conserva y se anota en `incidencias` |
| Fecha en formato dd/mm/aaaa | 2, 14, 22, 30 | 4 | 4 (convertidas a aaaa-mm-dd con fórmula) | 0 |  |
| Fecha inválida (mes 13\) | 7, 18 | 2 | 2 (`fecha_valida` \= FALSO, celda vacía) | 0 |  |
| Correo con mayúsculas | 2, 12, 27 | 3 | 3 (`MINUSC` \+ `ESPACIOS`) | 0 |  |
| Correo sin dominio | 5, 16 | 2 | 2 (`correo_valido` \= FALSO, celda vacía) | 0 |  |
| Teléfono con espacios | 2, 13 | 2 | 2 (espacios quitados con `SUSTITUIR`) | 0 |  |
| Teléfono incompleto | 19, 28 | 2 | 2 (`telefono_valido` \= FALSO, celda vacía) | 0 |  |
| Área con distinta capitalización | 2, 15, 23, 33 | 4 | 4 (primera letra mayúscula, resto minúscula) | 0 |  |
| Teléfono vacío | 24 | 1 | 1 (`telefono_valido` \= FALSO) | 0 |  |
| Empresa vacía | 17, 34 | 2 | 2 solo tras agregar la validación `empresa_completa` | Las 2 con las 4 validaciones originales | El laboratorio pide validar correo, teléfono, fecha y hora, pero no empresa: hubo que agregar una quinta validación |
| Hora fuera de horario | 5, 9, 21, 29, 36 | 5 | 5 detectadas (`hora_laboral` \= FALSO) | 0 | Se detectan pero **no se corrigen**: son los accesos inusuales que el análisis debe encontrar |
| Errores no listados en la clave (venían en la plantilla base) | 2 | 2 | 2 (hora `8:20` → `08:20`; motivo `supervision` → `Supervisión`) | 0 | Descubiertos al revisar la fila 2 |

## 3\. Verificación de anonimización

- Combinaciones `tipo_empresa + area + franja`: **11**; **4 aparecen una sola vez** (ids 16, 17, 34 y 36), es decir, 4 de 42 filas siguen siendo potencialmente identificables por quien conozca el contexto.  
- Dos de esas combinaciones únicas (ids 17 y 34\) se deben a datos faltantes (`Sin dato` en tipo\_empresa).  
- Las otras dos (ids 16 y 36\) son combinaciones raras dentro de Diseño \+ Oficina central; la del id 36 es además un acceso inusual (Madrugada): lo raro es a la vez lo más valioso para el análisis y lo más fácil de reidentificar.  
- Riesgo residual aceptado para este laboratorio; para producción habría que generalizar más (por ejemplo, agrupar Madrugada y Noche en "Fuera de horario") o suprimir esas filas.
