# Ficha inicial del proyecto

## Problema

{Ocurren emergencias de incendio y una alta tasa de falsas alarmas (provocadas por vapor, polvo o actividades de cocina). Esto genera respuestas tardías frente a incendios reales, evacuaciones desordenadas para los ocupantes y dificultad para detectar el peligro antes de que aparezcan las llamas.}

## Contexto

{Se desarrolla en edificios inteligentes dotados de infraestructura de Internet de las Cosas Artificial (AIoT), centralizada en sistemas de gestión de edificaciones (BMS), con sensores IoT multicriterio (temperatura, humo óptico, COV) y cámaras HD/térmicas.}

## Usuarios afectados

{Sufren el problema: Todos los individuos u ocupantes que se encuentran dentro del interior del edificio monitoreado.
Usarán la solución: El personal de gestión del edificio y los servicios de emergencia (bomberos), quienes recibirán alertas en tiempo real, guías de evacuación y modelos 3D del inmueble.
}

## Tipo de IA propuesto

{IA Predictiva. El sistema de igual manera requiere supervisión humana durante su funcionamiento para poder descartar anomalías o fallos del sistema ya que este posee la capacidad de analizar fotograma por fotograma y procesar flujos analógicos ruidosos en tiempo real para identificar patrones visuales, clasificar si hay fuego real frente a distractores y emitir diagnósticos predictivos de mantenimiento y riesgo}

## Qué dijeron los modelos

{Coincidieron en el uso de Redes Neuronales Convolucionales (CNN) y sensores IoT para reducir drásticamente las falsas alarmas.
Coincidieron en la necesidad de automatizar la respuesta mediante la integración con el sistema BMS (HVAC, iluminación dinámica y presurización).
Difirieron en el alcance del análisis espacial, destacando Gemini y Deepseek el uso de Gemelos Digitales para predecir la dinámica de fluidos, mientras ChatGPT priorizó la analítica continua del sensor de visión.}

## Primer riesgo identificado

{Privacidad de los usuarios, ya que el despliegue de cámaras de visión artificial dentro de las áreas del inmueble genera reparos sobre la privacidad de los ocupantes}

## Qué NO va a hacer la solución

{El proyecto NO va a prevenir, detectar ni resolver colapsos estructurales en la edificación, ya que el control de la integridad física de la estructura queda totalmente fuera de las manos de este sistema}
