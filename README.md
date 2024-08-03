# Analisis-Plantas-Energia-Solar

Este documento analiza los datos de una compañía de generación de energía solar fotovoltaica. Se han detectado comportamientos anómalos en dos de las plantas, y nuestro objetivo es identificar las causas de estos problemas.

## Objetivo

El objetivo es analizar los datos de las plantas solares para identificar problemas que afectan su rendimiento.

## Palancas Clave

1. **Irradiación**: Influye en la generación de corriente continua (DC). Un exceso de temperatura puede reducir la eficiencia.
2. **Estado de los Paneles**: Paneles limpios y funcionando correctamente son cruciales para maximizar la generación de DC.
3. **Eficiencia de Inverters**: La conversión de DC a corriente alterna (AC) debe ser eficiente para minimizar pérdidas.
4. **Medidores y Sensores**: Esenciales para monitorear y detectar fallos. Su mal funcionamiento puede comprometer el análisis.

## KPIs

- **Irradiación**: Energía solar que llega a los paneles.
- **Temperatura Ambiente y del Módulo**: Medida en grados Celsius.
- **Potencia DC**: Corriente continua medida en kW.
- **Potencia AC**: Corriente alterna medida en kW.
- **Eficiencia del Inverter**: Calculada como \( \text{Eficiencia} = \left(\frac{\text{AC}}{\text{DC}}\right) \times 100 \% \)

## Entidades y Datos

- **Celdas**: Unidad mínima de generación.
- **Módulos**: Celdas encapsuladas en estructuras rectangulares.
- **Paneles**: Compuestos por varios módulos.
- **Arrays**: Filas de paneles.
- **Inverters**: Transforman DC en AC.
- **Planta**: Conjunto de inverters, medidores y sensores.

## Granularidad de los Datos

Los datos se registran en ventanas de 15 minutos durante un período de 34 días. Las entidades disponibles son:

- **Plantas**: 2 plantas.
- **Inverters**: Varios inverters por planta.
- **Sensores**:
  - **Irradiación**: 1 sensor por planta.
  - **Temperatura Ambiente**: 1 sensor por planta.
  - **Temperatura del Módulo**: 1 sensor por planta.

**Nota**: Aunque se puede identificar el rendimiento de un inverter en una planta, no se puede determinar con precisión qué array, panel o módulo específico podría estar causando problemas.

## Análisis e Insights

### 4.2.1. Análisis de la Recepción de Energía Solar

**KPIs Utilizados**:
- Irradiación
- Temperatura Ambiente
- Temperatura del Módulo

Se ha creado un dataset con un inverter de cada planta para simplificar el análisis.

### 4.2.2. Diferencia en la Energía Recibida por Planta

**Conclusiones:**
- **Planta 2** recibe más energía solar que la Planta 1, pero esto no explica el problema de rendimiento observado.
- La correlación entre irradiación y temperatura ambiente no es tan alta como se esperaría, posiblemente debido a la variación de temperatura a lo largo del día.

**Conclusiones Adicionales:**
- La irradiación tiene una alta correlación con la temperatura del módulo.
- La irradiación correlaciona menos con la temperatura ambiente, aunque la correlación sigue siendo significativa.
- Se recomienda identificar módulos con baja generación de DC en condiciones de alta irradiación.

### 4.2.4. Análisis de la Irradiación y la Temperatura a lo Largo del Día

**Conclusiones:**
- La mayor irradiación ocurre entre las 11:00 y las 13:00.
- La irradiación cesa después de las 18:00.
- La temperatura máxima ocurre entre las 14:00 y las 16:00, mostrando un retraso respecto a la máxima irradiación, que se da a las 12:00.

### 4.2.5. Análisis de la Irradiación frente a la Energía DC Generada

**Conclusiones:**
- La Planta 2 muestra una producción de energía DC mucho menor que la Planta 1, incluso con niveles similares de irradiación.
- La relación entre irradiación y kW generados es inconsistente. La producción de kW no sigue una tendencia lógica con la irradiación, y los datos de acumulación parecen tener inconsistencias.

**INSIGHT #1:** La Planta 2 genera niveles mucho más bajos de DC incluso con niveles similares de irradiación.

### 4.2.6. Generación de Energía a lo Largo del Día

**Conclusiones:**
- La Planta 1 muestra mayor variabilidad en la generación de DC, mientras que la Planta 2 es más constante.
- La Planta 2 presenta niveles de generación de DC constantes, pero aproximadamente diez veces inferiores a los de la Planta 1.

**INSIGHT #2:** Los niveles bajos de DC en la Planta 2 son constantes y sus curvas diarias parecen normales.

## 4.3. Conclusiones Finales

**Problemas Identificados:**
- Existen graves problemas de calidad de datos que deben revisarse, incluidos los medidores de las plantas.
- La diferencia en la generación de DC (10 veces superior en la Planta 1) y la baja eficiencia en la Planta 1 sugieren que los datos de generación de DC pueden estar escalados artificialmente.
- Ambas plantas reciben una cantidad adecuada de irradiación, y no se ha encontrado un problema significativo en esta fase.
- La temperatura ambiente más alta en la Planta 2 no parece impactar significativamente en la generación de energía.

**Insights Específicos:**
- **INSIGHT #3:** La Planta 1 tiene una baja capacidad de transformación de DC a AC (alrededor del 10%), lo cual sugiere problemas con los inverters.
- **INSIGHT #4:** En la Planta 2, varios inverters muestran una falta de producción de DC, indicando que algunos módulos necesitan revisión.
- **INSIGHT #5:** A pesar de la falta de generación de DC en algunas horas, los inverters de la Planta 2 funcionan bien en términos de eficiencia de transformación a AC.

**Recomendaciones:**
1. Revisar la calidad de los datos y la fiabilidad de los medidores.
2. Realizar una revisión de mantenimiento en los módulos de los inverters en la Planta 2 con alta incidencia de generación cero de DC.
3. Revisar el mantenimiento de los inverters de la Planta 1 para mejorar la eficiencia de conversión de DC a AC.

---

Este análisis se basa en la suposición de que los datos de DC y AC son correctos, a pesar de las anomalías observadas. Se recomienda una revisión adicional con expertos para confirmar estas conclusiones y resolver cualquier problema de datos.







