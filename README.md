# Predicción del Valor del Ciclo de Vida del Cliente (CLTV)

Este repositorio contiene el código y los recursos para predecir el Valor del Ciclo de Vida del Cliente (CLTV) utilizando datos de transacciones. Se aplican técnicas de análisis exploratorio de datos (EDA), ingeniería de características (feature engineering) y modelos probabilísticos para estimar el valor que un cliente aportará a un negocio a lo largo de su relación.

## Contenido

*   [Descripción del Proyecto](#descripcion-del-proyecto)
*   [Conjunto de Datos](#conjunto-de-datos)
*   [Análisis Exploratorio de Datos (EDA)](#analisis-exploratorio-de-datos-eda)
*   [Ingeniería de Características (Feature Engineering)](#ingenieria-de-caracteristicas-feature-engineering)
*   [Modelado](#modelado)
    *   [Modelos Probabilísticos (BG/NBD, Gamma-Gamma)](#modelos-probabilisticos-bgnbd-gamma-gamma)
        *   [Beta-Geométrica/Distribución Binomial Negativa (BG/NBD)](#beta-geometricadistribucion-binomial-negativa-bgnbd)
        *   [Modelo Gamma-Gamma](#modelo-gamma-gamma)
*   [Uso](#uso)
*   [Dependencias](#dependencias)
*   [Resultados](#resultados)
*   [Contribuciones](#contribuciones)

## Descripción del Proyecto

Este proyecto busca predecir el CLTV, una métrica crucial para la gestión de relaciones con el cliente (CRM). Al predecir el valor futuro de los clientes, las empresas pueden tomar decisiones informadas sobre estrategias de marketing, retención y adquisición.

## Conjunto de Datos

El conjunto de datos utilizado en este proyecto contiene información sobre las transacciones de clientes, incluyendo:

*   `CustomerID`: Identificador único del cliente.
*   `InvoiceDate`: Fecha de la factura.
*   `InvoiceNo`: Número de la factura.
*   `MonetaryValue`: Valor monetario de la transacción.

(Añade más detalles sobre las columnas relevantes de tu dataset)

## Análisis Exploratorio de Datos (EDA)

El análisis exploratorio de datos se centra en comprender las características del conjunto de datos. Las tareas principales incluyen:

*   **Estadísticas descriptivas:** Media, mediana, desviación estándar, etc., de las variables clave.
*   **Visualizaciones:** Histogramas, diagramas de dispersión, etc., para identificar patrones y distribuciones.
*   **Identificación de valores atípicos (outliers):** Uso de boxplots u otros métodos para detectar valores extremos.

En particular, se presta atención a la distribución de la variable `MonetaryValue`, que a menudo presenta asimetría positiva.

## Ingeniería de Características (Feature Engineering)

A partir de los datos de transacciones, se crean las siguientes características para el modelado de CLTV:

*   `Recency`: Tiempo transcurrido desde la última compra del cliente (en días).
*   `Frequency`: Número total de compras realizadas por el cliente.
*   `T` (Tiempo): Tiempo transcurrido desde la primera compra del cliente (en días).
*   `MonetaryValue`: Valor monetario promedio de las compras del cliente.

Se aplican transformaciones logarítmicas a `MonetaryValue` para reducir la asimetría y mejorar el rendimiento del modelo. Adicionalmente, se considera el uso de winsorización para mitigar el impacto de valores atípicos extremos.

## Modelado

### Modelos Probabilísticos (BG/NBD, Gamma-Gamma)

Se utilizan modelos probabilísticos específicos para la predicción de CLTV, que se adaptan bien a la naturaleza de los datos de transacciones.

#### Beta-Geométrica/Distribución Binomial Negativa (BG/NBD)

El modelo BG/NBD modela dos procesos:

*   **Proceso de compra:** Modelado con una distribución Binomial Negativa, que representa el número de transacciones que un cliente realizará en un período de tiempo.
*   **Proceso de abandono:** Modelado con una distribución Beta-Geométrica, que representa la probabilidad de que un cliente se vuelva inactivo (abandone).

#### Modelo Gamma-Gamma

El modelo Gamma-Gamma se utiliza para estimar el valor monetario promedio de las transacciones de un cliente, dado que está "vivo" (es decir, aún realiza compras). Asume que el valor monetario de las transacciones sigue una distribución Gamma.



## Resultados

(Incluir ejemplos de los resultados obtenidos, como métricas de evaluación o visualizaciones de las predicciones de CLTV.)

## Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue o un pull request si tienes alguna sugerencia o mejora.
