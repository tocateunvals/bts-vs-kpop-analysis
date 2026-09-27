# Diccionario de Variables

## Dataset: Kpop Artists and Full Spotify Discography

**Fuente:** [Kaggle - ericwan1/kpop-artists-and-full-spotify-discography](https://www.kaggle.com/datasets/ericwan1/kpop-artists-and-full-spotify-discography)

**Archivo principal:** `album_to_track_df.csv`

**Dimensiones:** 16,330 filas × 20 columnas

**Descripción:** Dataset con información de tracks de 206 artistas de K-pop, incluyendo 13 características de audio extraídas de la API de Spotify.

---

## Variables identificadoras (categóricas)

| Variable | Tipo | Descripción | Ejemplo |
| :--- | :--- | :--- | :--- |
| `Unnamed: 0` | int64 | Índice del CSV (ruido, se elimina en limpieza) | 0, 1, 2, ... |
| `Artist` | str | Nombre del artista o grupo | "BTS", "H.O.T." |
| `Artist_Id` | str | ID único del artista en Spotify | "5JrfgZAgqAMywJpLpJM0eS" |
| `Album_Name` | str | Nombre del álbum | "BE", "Wings" |
| `Album_Id` | str | ID único del álbum en Spotify | "697cPaD568S5Zt4bgo4cQf" |
| `Track_Title` | str | Título de la canción | "Opening - Live", "Dynamite" |
| `Track_Id` | str | ID único del track en Spotify | "6K0n7RweqUBSZWoKKkHFrb" |

## Variables de audio (numéricas continuas)

| Variable | Tipo | Rango | Descripción |
| :--- | :--- | :--- | :--- |
| `danceability` | float64 | 0.0 - 1.0 | Qué tan bailable es el track (basado en tempo, ritmo, estabilidad). 1 = muy bailable. |
| `energy` | float64 | 0.0 - 1.0 | Intensidad y actividad percibida. 1 = muy enérgico (tipo death metal). |
| `key` | float64 | 0 - 11 | Tonalidad musical (0=Do, 1=Do#, 2=Re, ..., 11=Si). |
| `loudness` | float64 | -60 a 0 (dB) | Volumen general del track en decibeles. Valores más cercanos a 0 = más fuerte. |
| `mode` | float64 | 0 o 1 | Modalidad musical: 0 = menor, 1 = mayor. |
| `speechiness` | float64 | 0.0 - 1.0 | Presencia de palabras habladas. >0.66 = probablemente hablado, <0.33 = probablemente música. |
| `acousticness` | float64 | 0.0 - 1.0 | Confianza de que el track sea acústico. 1 = totalmente acústico. |
| `instrumentalness` | float64 | 0.0 - 1.0 | Predice si el track no tiene voces. >0.5 = probablemente instrumental. |
| `liveness` | float64 | 0.0 - 1.0 | Detecta presencia de audiencia en vivo. >0.8 = probablemente en vivo. |
| `valence` | float64 | 0.0 - 1.0 | Positividad musical. 1 = alegre/euforico, 0 = triste/enojado. |
| `tempo` | float64 | 0 - 250 (BPM) | Velocidad estimada del track en beats por minuto. |
| `duration_ms` | float64 | milisegundos | Duración del track (se convertirá a minutos en limpieza). |
| `time_signature` | float64 | 3 - 7 | Compás musical estimado (cantidad de tiempos por compás). Habitualmente 4. |

---

## Observaciones

- **`Unnamed: 0`** es solo el índice del CSV. Se debe eliminar en la limpieza.
- **`key`, `mode` y `time_signature`** están almacenadas como `float64`, pero conceptualmente son **categóricas**.
- **`duration_ms`** está en milisegundos y debería convertirse a minutos para interpretación.
- **No hay columna de popularidad ni de oyentes.** Para analizar popularidad será necesario complementar con otro dataset de Spotify.
- Se detectaron **~62 `Track_Id` duplicados** que habrá que tratar en la limpieza.

---

## Preguntas de investigación del proyecto

1. ¿Cómo han evolucionado las características de audio de BTS a lo largo de su carrera?
2. ¿Existen diferencias significativas en las propiedades de audio entre BTS y otros artistas de K-pop?
3. (Por definir) Análisis de popularidad — sujeto a la incorporación de otro dataset.