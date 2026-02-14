# EMG ANALISIS DE LA SEÑAL Y VISUALIZACIÓN

---

## METADATA – Descripción de los datos

### 1. Descripción de los datos

El dataset contiene señales electromiográficas (EMG) adquiridas mediante electrodos superficiales conectados a un módulo AD8232 y digitalizadas a 1 kHz utilizando un microcontrolador STM32.

Cada registro representa una medición de diferencia de potencial en milivoltios correspondiente a la actividad eléctrica muscular en un instante de tiempo determinado correspondientes a estados de reposo y contracción muscular voluntaria.

Las señales fueron almacenadas para su posterior análisis en Python con el objetivo de caracterizar estadísticamente la activación muscular y validar el procesamiento digital implementado en el sistema embebido.

### 2. Diccionario de Datos

time ------------------------ Tiempo en segundos  
emg1 ------------------------ Señal EMG músculo 1 (mV)  
state ------------------------ Estado muscular: reposo / low-contraction / contracción  
sample_id ------------------------ Número de muestra único para cada lectura  
muscle ------------------------ Nombre del músculo donde se tomó la señal EMG (Bicep, Tricep, Cuadriceps, Deltoides, Pectorales, Dorsales, Trapecio superior, Flexores muñeca)  
patience_age ------------------------ Edad de la persona en años al momento de la toma de la señal EMG  
patience_sex ------------------------ F / M  
emg_raw ------------------------ Señal EMG cruda medida por el ADC (0–4095)  
emg_rect  ------------------------ Señal EMG rectificada, tomando el valor absoluto con el offset 2048: |emg_raw - 2048|  
emg_voltage  ------------------------ Conversión de la señal EMG cruda a voltaje: V=(ADC/4095)*3.3  
contraction % ------------------------ Contracción relativa en porcentaje respecto al máximo de ese músculo y paciente   
date ------------------------ Fecha y hora de la toma de la señal EMG (dd/mm/aaaa hh:mm:ss)


## OBJETIVO ANALITICO
### 1. objetivo

Analizar el comportamiento estadístico y temporal de señales EMG para determinar si es posible discriminar estados de reposo y contracción muscular a partir de métricas cuantitativas como amplitud, varianza y RMS.

### 2. Pregunta problema

¿La señal EMG permite identificar de manera clara y consistente los períodos de contracción muscular respecto al reposo?

### 3. Hipótesis

H1: El valor RMS de la señal EMG es mayor durante contracción que en reposo.

H2: La varianza de la señal aumenta significativamente en estado de activación muscular.

H3: Si se registran dos músculos simultáneamente, existe correlación positiva durante contracción conjunta.

