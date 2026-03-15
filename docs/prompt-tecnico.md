# Prompt técnico: visualización generativa con boyas NOAA

Diseña un sistema de visualización generativa que utilice los datos en tiempo real de las boyas del **National Data Buoy Center (NOAA)** disponibles en [https://www.ndbc.noaa.gov](https://www.ndbc.noaa.gov).

El sistema debe consultar periódicamente la **última lectura disponible de cada boya** y generar automáticamente una **escena visual oceánica asociada a esa estación**.

Cada boya debe representarse como una **unidad visual autónoma**, donde los datos meteorológicos y oceanográficos determinan el estado del entorno visual.

El sistema funciona exclusivamente como **capa de visualización dinámica**, no como simulación física completa.

## Modelo conceptual

Cada boya se transforma en una **escena oceánica viva** que refleja el estado actual del mar en ese punto del planeta.

El sistema consulta los datos más recientes y genera una imagen o escena donde el océano puede verse:

- tranquilo
- agitado
- tormentoso
- cubierto de niebla
- iluminado por amanecer o atardecer
- congelado o tropical

dependiendo de las variables ambientales registradas por la boya.

## Variables de datos y su interpretación visual

- **Dirección y velocidad del viento**: determina dirección de olas, partículas atmosféricas y movimiento de nubes.
- **Ráfagas de viento**: generan picos de turbulencia visual o aparición de tormentas.
- **Presión atmosférica**: presión baja produce tormentas y cielos oscuros; presión alta produce cielos despejados.
- **Temperatura del agua**: modifica color del océano (azul profundo, verde tropical, gris frío).
- **Temperatura del aire**: determina iluminación ambiental y tipo de atmósfera.
- **Punto de rocío y humedad**: controla presencia de neblina, nubes bajas o lluvia.
- **Altura del oleaje (cuando esté disponible)**: modifica amplitud y energía de las olas.

## Lógica temporal

El sistema siempre utiliza:

**la última lectura disponible de cada boya consultada.**

Cada actualización genera una **nueva versión de la escena**.

No se requiere interpolación compleja; el objetivo es mostrar **el estado actual del océano según la red de sensores.**

## Arquitectura de visualización

El sistema debe poder mostrar:

- una escena por boya
- múltiples boyas simultáneamente
- un mapa global donde cada nodo es una escena oceánica

Cada nodo visual es una **interpretación artística de los datos oceanográficos en tiempo real**.

## Estética visual

Las escenas deben mantener coherencia visual entre sí, como si todas pertenecieran a un mismo universo oceánico.

Inspiraciones visuales:

- visualización científica
- simulación meteorológica
- arte generativo oceánico
- paisajes marinos dinámicos

## Objetivo conceptual

Transformar la red global de sensores oceánicos en una **constelación de paisajes marinos vivos**, donde cada boya revela el estado actual del océano mediante una representación visual generativa.
