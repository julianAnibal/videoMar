# videoMar

`videoMar` define un sistema de visualización generativa para convertir lecturas en tiempo real de boyas NOAA/NDBC en escenas oceánicas dinámicas.

## Prompt técnico base

Diseñar un sistema de visualización generativa que use datos en tiempo real de boyas del **National Data Buoy Center (NOAA)** ([ndbc.noaa.gov](https://www.ndbc.noaa.gov)).

- El sistema consulta periódicamente la **última lectura disponible** de cada boya.
- Cada boya genera una **escena visual oceánica autónoma**.
- El producto es una **capa de visualización dinámica**, no una simulación física completa.

Ver el detalle completo en [`docs/prompt-tecnico.md`](docs/prompt-tecnico.md).

## Arquitectura propuesta

La arquitectura para `Synth+Mar` se divide en 5 bloques:

1. **Pipeline de datos NOAA**
2. **Motor de estado visual por boya**
3. **Renderizador generativo**
4. **Atlas global de boyas**
5. **Integración sonora opcional**

Ver diseño detallado en [`docs/arquitectura-synth-mar.md`](docs/arquitectura-synth-mar.md).

## Próximos pasos

- Definir stack visual (WebGL/Three.js, Unity, Unreal o TouchDesigner).
- Seleccionar formato de ingestión NOAA (stdmet, latest obs, JSON/XML disponible por estación).
- Prototipar 3 estilos visuales coherentes para diferentes estados del mar.
- Construir un MVP con 5-10 boyas en paralelo.
