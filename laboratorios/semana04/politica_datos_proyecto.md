# Política de datos del proyecto Estimador de Inmuebles con IA

## 1. Alcance
Esta política cubre los ocho datos del inventario del proyecto:
- D1 Nombre del usuario (personal)
- D2 Correo electrónico (personal)
- D3 Ubicación exacta del inmueble (personal, mayor riesgo)
- D4 Fotografías de fachadas (personal)
- D5 Registros de acceso (personal)
- D6 Ingreso mensual declarado (sensible)
- D7 Estimación de valor generada por el modelo (personal)
- D8 Catálogo de materiales y estilos (no personal)

## 2. Ciclo de vida
El detalle está en `ciclo_vida_dato_proyecto.drawio` (y su `.png`). Las seis etapas y sus responsables son:
1. Captura: Responsable de producto.
2. Almacenamiento: Administrador del sistema.
3. Uso: Líder de datos e IA.
4. Compartición: Oficial de privacidad.
5. Retención: Oficial de privacidad.
6. Eliminación: Administrador del sistema.
El dato de mayor riesgo (D3) pasa por cuatro terceros: proveedor de nube, API de modelo generativo, servicio de mapas y servicio de respaldos.

## 3. Normativa aplicable
Aplican tres marcos, según `matriz_cumplimiento_proyecto.xlsx`:
- LFPDPPP de México (ley publicada el 20 de marzo de 2025): obligatoria. Rige consentimiento, aviso de privacidad, proporcionalidad, retención y el derecho de oposición a decisiones automatizadas (Art. 26, fr. II).
- Ley de IA de la UE: obligatoria solo en transparencia (Art. 50); el resto se adopta como buena práctica porque el proyecto no se clasifica como alto riesgo.
- NIST AI RMF: voluntario; se usa como guía de gestión de riesgo (Gobernar, Mapear, Medir, Gestionar).

## 4. Controles comprometidos
- Aviso de IA, consentimiento por finalidad y aviso de privacidad: Responsable de producto.
- Captura mínima y borrado de EXIF: Responsable de producto.
- Cifrado en reposo, acceso por rol con doble factor y registro de accesos: Administrador del sistema.
- Registro de riesgos, revisión humana de estimaciones y prueba de sesgos: Líder de datos e IA.
- Contratos con proveedores y anonimización antes de enviar datos: Oficial de privacidad.
- Plazos de retención (12 meses; logs 6 meses) y borrado seguro con constancia: Oficial de privacidad y Administrador del sistema.
- Canal de oposición y revisión humana: Líder de datos e IA.

## 5. Manejo de datos con herramientas de IA
Aplica a ChatGPT, Gemini, Deepseek, Dify y cualquier herramienta similar.
- Prohibido ingresar D1, D2, D3, D4, D5, D6 y D7 reales. En especial, nunca D3 ni D6.
- Permitido ingresar D8 y datos ficticios generados a mano con la misma estructura que los reales.
- Permitido ingresar datos anonimizados (sin nombre, correo, dirección ni fotos reales), solo si se verificó que no permiten identificar a nadie al combinarse.
- Antes de pegar cualquier texto, revisarlo contra el inventario; ante la duda, tratarlo como dato real y no pegarlo.
- Los resultados del modelo no se citan ni se copian como hecho sin verificarlos en la fuente oficial.
- Todo uso de IA se registra en la declaración de uso de IA del reporte.

## 6. Revisión
Esta política se revisa cada trimestre y cada vez que cambie un proveedor, un dato del inventario o la normativa. La aprueba el Líder del proyecto con el visto bueno del Oficial de privacidad.
