# Arquitectura propuesta para Synth+Mar

## 1) Motor visual

### Objetivo
Renderizar una micro-escena oceánica por boya con coherencia estilística global.

### Requisitos
- Render en tiempo real (2D/3D).
- Parámetros de escena actualizables por eventos de datos.
- Sistema de materiales y atmósfera parametrizable.

### Mapeo de parámetros
- `wind_dir`, `wind_speed` -> dirección y energía del campo de olas.
- `gust` -> ráfagas puntuales de partículas y deformación de superficie.
- `air_pressure` -> densidad de nubes / oscuridad del cielo.
- `water_temp` -> paleta cromática del mar.
- `air_temp` y `dew_point` -> color de luz ambiente y niebla.
- `wave_height` -> amplitud de desplazamiento de la malla.

## 2) Pipeline de datos NOAA

### Fuente
NDBC NOAA: consultas por estación y lectura más reciente.

### Flujo
1. Descubrir lista de estaciones objetivo.
2. Consultar endpoint de última observación por estación.
3. Normalizar unidades y manejar valores faltantes.
4. Publicar un `state snapshot` por boya.

### Contrato de datos sugerido
```json
{
  "station_id": "41009",
  "timestamp": "2026-03-15T01:20:00Z",
  "wind_dir_deg": 120,
  "wind_speed_ms": 7.4,
  "gust_ms": 10.2,
  "air_pressure_hpa": 1008.3,
  "air_temp_c": 18.1,
  "water_temp_c": 22.4,
  "dew_point_c": 16.0,
  "humidity_pct": 82,
  "wave_height_m": 1.4
}
```

## 3) Sistema de actualización

### Política temporal
- Siempre usar **última lectura disponible**.
- Frecuencia sugerida: 1-5 minutos, configurable por estación.
- Si no hay nuevos datos, conservar último estado y marcar `stale`.

### Eventos
- `station_state_updated`
- `station_state_stale`
- `station_state_missing`

## 4) Atlas global de boyas

### Vistas
- **Grid de escenas**: una miniatura viva por estación.
- **Modo foco**: escena ampliada de una boya.
- **Mapa global**: nodos geolocalizados con transición visual en tiempo real.

### Escalabilidad
- Render distribuido por tiles/regiones.
- Carga perezosa de escenas fuera del viewport.
- Límite dinámico de FPS según carga.

## 5) Integración sonora (opcional)

### Síntesis sugerida
- `wind_speed` -> ruido filtrado y modulación.
- `wave_height` -> capa de graves y swell.
- `air_pressure` -> brillo armónico general.
- `humidity` -> densidad de reverb/ambiente.

### Resultado
Un paisaje audiovisual donde cada boya funciona como voz de un instrumento oceánico distribuido.

## MVP recomendado

1. Seleccionar 5-10 estaciones de regiones distintas.
2. Implementar fetch + normalización + estado local.
3. Renderizar escena simple (cielo, mar, niebla, partículas).
4. Añadir vista mapa con nodos y color por estado.
5. Incorporar transiciones suaves entre snapshots consecutivos.
