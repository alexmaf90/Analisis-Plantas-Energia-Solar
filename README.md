# Analisis-Plantas-Energia-Solar

En este caso se analizarán los datos de una compañía de generación de energía solar fotovoltaica.

Se han detectado comportamientos anómalos en 2 de las plantas tras nuestro análisis trataremos de identificar el motivo.

Analizaremos los datos de los sensores y medidores para ver si podemos detectar el problema.

## Objetivo
Analizar los datos de las plantas solares para identificar problemas que afectan su rendimiento.

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

## Conclusiones del Análisis de Calidad de Datos

### Planta 1

#### Datos de Generación
- **Desviación en DC y AC**: La diferencia entre las medias de DC y AC es significativa. Los inverters están transformando solo el 10% de DC a AC, lo cual es muy bajo.
- **Inverters**: La planta tiene 22 inverters, todos con un número similar de medidas, pero algunas diferencias podrían deberse a mantenimientos o pérdidas de datos.
- **Periodo de Datos**: Datos disponibles entre el 15 de mayo y el 17 de junio de 2020, con todos los días cubiertos, aunque algunos días (como el 21/05 y el 29/05) tienen menos mediciones. La regularidad no es total.

### Planta 2

#### Datos de Generación
- **Desviación en DC y AC**: Los valores de DC y AC están mucho más cercanos entre sí en comparación con la Planta 1. El ratio de conversión está más cercano a 1.
- **Inverters**: La planta tiene 22 inverters, con la mayoría teniendo un número similar de medidas. Sin embargo, 4 inverters tienen unas 800 medidas menos.
- **Periodo de Datos**: Datos disponibles entre el 15 de mayo y el 17 de junio de 2020, con todos los días cubiertos, pero algunos días (como el 20/05) tienen menos mediciones. La regularidad no es total.






