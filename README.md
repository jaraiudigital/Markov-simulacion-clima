# 🌧️ Simulador HMM del Clima de Medellín

Simulador interactivo de clima usando Modelos Ocultos de Markov (HMM) para la ciudad de Medellín, Colombia.

## 📋 Descripción

Este programa simula el comportamiento climático mensual basado en niveles de humedad. Utiliza distribuciones de probabilidad para modelar transiciones entre estados (humedad baja, media, alta) y las observaciones climáticas resultantes (soleado, lluvia, tormenta).

**Características principales:**
- ❌ Sin semilla fija → cada ejecución es diferente (aleatorio real)
- 📊 Control total del número de simulaciones
- 📈 Estadísticas con intervalos de confianza
- 📉 Gráficos de distribución y convergencia
- 🗺️ Diagrama de estados con probabilidades decimales

## 🗓️ Meses disponibles

| Mes | Días | Días lluvia | Humedad |
|-----|------|-------------|---------|
| Junio | 30 | 21 | 82% |
| Julio | 31 | 19 | 78% |
| Agosto | 31 | 20 | 79% |
| Septiembre | 30 | 21 | 83% |
| Octubre | 31 | 23 | 85% |
| Noviembre | 30 | 20 | 80% |
| Diciembre | 31 | 14 | 72% |

## 🚀 Instalación

### Requisitos
- Python 3.8 o superior

### Pasos

1. **Clonar o descargar** el archivo 

2. **Instalar dependencias:**
```bash
pip install numpy pandas matplotlib seaborn
Ejecutar el programa:

bash
python simulador_clima.py
💻 Cómo usarlo
Al ejecutar el programa:

Selecciona un mes (1-7)

Elige número de simulaciones (1-1000, Enter para 30)

Elige días por simulación (Enter para mes completo)

El programa mostrará:

Las matrices de probabilidad (transición y emisión)

Diagrama de transición de estados

Resultados estadísticos

6 gráficos de análisis

📊 Ejemplo de salida
text
📈 RESULTADOS AGREGADOS
   🌧️ Días lluviosos promedio:     22.3 ± 1.8 días
   ⛈️ Días tormenta promedio:      7.1 ± 1.5 días
   ☀️ Días soleados promedio:      8.7 ± 1.6 días
   💧 Proporción de lluvia:        71.9% ± 5.8%
   📊 Intervalo confianza 90%:     [63.8%, 79.5%]

🎯 Comparación con datos reales:
   Lluvia real:        74.2%
   Lluvia simulada:    71.9%
   ✅ Excelente! El modelo es muy preciso.
📊 Gráficos generados
Diagrama de transición de estados

Distribución de días lluviosos

Distribución de días con tormenta

Boxplot de proporción de lluvia

Curva de convergencia de la media

Distribución de niveles de humedad

🔬 Cómo funciona
Estados ocultos (humedad)
HB (Humedad Baja) → Días soleados ☀️

HM (Humedad Media) → Lluvias ligeras 🌧️

HA (Humedad Alta) → Tormentas ⛈️

Matrices de probabilidad
Transición (A): Probabilidad de cambiar entre estados de humedad
Emisión (B): Probabilidad de observar cada clima según el estado
Inicial (π): Probabilidad de empezar en cada estado

Algoritmo
python
# Para cada simulación:
1. Elegir estado inicial según π
2. Elegir observación según B[estado]
3. Para cada día siguiente:
   - Nuevo estado según A[estado_actual]
   - Nueva observación según B[nuevo_estado]
4. Repetir N veces
5. Calcular estadísticas
🎯 Validación
Las matrices se ajustan según la humedad promedio real de Medellín:

Muy húmedo (≥80%): Junio, Septiembre, Octubre

Húmedo (75-79%): Julio, Agosto, Noviembre

Seco (<75%): Diciembre

El error típico es menor al 5% comparado con datos reales.

📁 Estructura del código
python
class HiddenMarkovModel:
    - __init__()      # Inicializa matrices
    - generar_secuencia()  # Una simulación
    - simular_multiples()   # Múltiples simulaciones
    - graficar_diagrama_estados_pequeno()
    - graficar_distribucion_simulaciones()
🧪 Ejemplo de aleatoriedad
Sin semilla fija, cada ejecución da resultados diferentes:

bash
# Ejecución 1: 71.9% lluvia
# Ejecución 2: 73.2% lluvia  
# Ejecución 3: 70.8% lluvia
¡Esto refleja la variabilidad natural del clima!

❓ Preguntas frecuentes
¿Por qué sin semilla fija?
Para simular la aleatoriedad real del clima. Cada ejecución es única.

¿Cuántas simulaciones recomiendas?
30-100 para resultados estables, 500+ para alta precisión.

¿Se puede usar para otros meses?
Sí, modificando las matrices de probabilidad.

¿Los datos son reales?
Sí, basados en promedios históricos de Medellín.

📝 Requisitos técnicos
text
Python 3.8+
numpy
pandas  
matplotlib
seaborn
👥 Autores
Jorge Jaramillo

Johan Orrego

Fecha: mayo 2026

📄 Licencia
MIT License - Uso libre para fines educativos y de investigación.

🙏 Agradecimientos
Datos climáticos: IDEAM Colombia
Inspiración teórica: Rabiner (1989) - "A tutorial on Hidden Markov Models"
