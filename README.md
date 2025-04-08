# machine_learning
Noteebooks de algoritmos usados en Módulo 10 del Máster en Python Avanzado

# Análisis Avanzado de Fútbol - Atlético de Madrid

Este proyecto implementa dos modelos de análisis avanzado usando como ejemplo datos abiertos de los partidos de liga del Club Atlético de Madrid:

1. **Predicción de Modelo de Juego**: Usando SVM para clasificar y predecir patrones tácticos.
2. **Recomendación de Jugadores Similares**: Empleando técnicas de clustering y KNN para encontrar jugadores con características estadísticas similares.

## Tabla de Contenidos
- [Requisitos](#requisitos)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Modelo 1: Predicción de Modelo de Juego](#modelo-1-predicción-de-modelo-de-juego)
- [Modelo 2: Recomendación de Jugadores Similares](#modelo-2-recomendación-de-jugadores-similares)
- [Uso](#uso)
- [Limitaciones](#limitaciones)
- [Trabajos Futuros](#trabajos-futuros)

## Requisitos


## Bibliotecas requeridas
-pandas==1.5.3
-numpy==1.23.5
-scikit-learn==1.2.2
-matplotlib==3.7.1
-seaborn==0.12.2

## Estructura del Proyecto

├── assets/
│   ├── players/          # Imágenes de jugadores
│   └── escudos/          # Escudos de equipos
├── data/
│   ├── general.csv       # Estadísticas de jugadores de campo
│   ├── porteros.csv      # Estadísticas de porteros
│   ├── mercado.csv       # Valores de mercado y contratos
│   ├── atletico.csv      # Plantilla del Atlético de Madrid
│   └── equipos.csv       # Información de equipos
├── modelo_juego.ipynb       # Modelo 1: Predicción de modelo de juego (SVM)
├── similar_players.ipynb    # Modelo 2: Recomendación de jugadores similares
└── README.md

# Modelo 1: Predicción de Modelo de Juego

### 1. Descripción:

- Este modelo utiliza Support Vector Machines (SVM) para clasificar y predecir patrones tácticos basados en métricas de rendimiento del equipo. El objetivo es identificar el enfoque táctico más efectivo contra diferentes tipos de rivales.

### 2. Características:

- Clasificación Multiclase: Identifica 4 modelos de juego distintos (posesión, presión alta, contraataque, juego directo);
- Análisis de Importancia: Evalúa qué métricas tienen mayor impacto en el éxito de cada modelo de juego;
- Visualización Táctica: Genera mapas de calor y gráficos de radar para representar patrones tácticos.

### 3. Métricas de Evaluación:

- Precisión: 78.5%;
- Recall: 76.3%;
- F1 Score: 77.2%;
- Matriz de Confusión Normalizada.

# Modelo 2: Recomendación de Jugadores Similares

### 1. Descripción:

- Este sistema combina técnicas de clustering (K-Means) y K-Nearest Neighbors (KNN) para identificar jugadores con características estadísticas similares a los de la plantilla del Atlético de Madrid, facilitando la identificación de posibles fichajes.

### 2. Pipeline de Análisis:

-Limpieza de Datos: Normalización de nombres, manejo de valores faltantes y estandarización;

-Ingeniería de Características: Creación de métricas específicas por posición;

-Clustering con K-Means: Agrupación de jugadores en perfiles similares;

-Búsqueda de Similitud con KNN: Identificación de jugadores más similares a cada referencia;

-Visualización de Resultados: Representación gráfica con comparativas estadísticas.

### 3. Métricas Generadas por Posición:

- Porteros (GK): Eficiencia de paradas, porcentaje de porterías a cero, rendimiento vs. esperado;

- Defensas (DF): Contribución defensiva, eficiencia de pases, acciones defensivas por 90';

- Centrocampistas (MF): Creación de juego, progresión, contribución defensiva;

- Delanteros (FW): Efectividad de ataque, precisión de disparo, eficiencia ofensiva.

### 4. Evaluación

- Silhouette Score: Medida de cohesión de clusters (valores entre 0.15-0.25);

- Distancia Media: Cercanía estadística entre jugadores similares;

- Validación Cualitativa: Comprobación por expertos futbolísticos de la coherencia de recomendaciones.


# Uso

## Modelo 1: Predicción de Modelo de Juego

''' from modelo_juego import predecir_modelo_juego_
    #Predecir modelo de juego óptimo contra un rival específico
    rival = "Real Madrid"
    modelo_recomendado = predecir_modelo_juego(rival, df_partidos, df_equipos)
    print(f"Modelo de juego recomendado contra {rival}: {modelo_recomendado}")'''

## Modelo 2: Recomendación de Jugadores Similares

'''from similar_players import ejecutar_analisis_completo, visualizar_jugador_similares
    # Ejecutar análisis completo
    resultados = ejecutar_analisis_completo()'''

'''# Buscar jugadores similares a un específico
    from similar_players import entrenar_modelo_knn
    recomendaciones = entrenar_modelo_knn(
        "Griezmann", 
        resultados["resultado_clusters"], 
        df_atletico, 
        df_general, 
        df_porteros, 
        df_mercado, 
        df_equipos,
        top_n=5
    )'''

''' # Visualización personalizada
    visualizar_jugador_similares("Griezmann", recomendaciones, top_n=5)'''

## Limitaciones

- Los modelos están limitados por la calidad y completitud de los datos disponibles;
- No se consideran factores intangibles como liderazgo, adaptabilidad cultural o factores psicológicos;
- Las estadísticas están influenciadas por el contexto táctico de cada equipo;
- El rendimiento pasado no garantiza rendimiento futuro.

## Trabajos Futuros

- Incorporación de datos de tracking y GPS para análisis posicional;
- Expansión del modelo para incluir análisis de video;
- Implementación de una interfaz web para el departamento de scouting;
- Integración con sistemas de información de rendimiento en tiempo real;
- Incorporación de análisis de redes sociales para evaluar impacto mediático.