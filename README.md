# ML Framework y sin Framework

Este proyecto contiene código de Machine Learning sin utilizar frameworks externos y la opcion de ejecutarlo con framework externo.


## Cómo correr el código
1. **Clona el repositorio**

23. **Ejecuta el script principal:**
    ```bash
    python main.py
    ```

3. **Responde las preguntas que te hara el codigo (seleccion de modelo KNN con framework o sin Framework):**
   
## Estructura del proyecto

- `main.py`: Script principal para ejecutar el código con las implementaciones

## Requisitos

1. **Instala las librerias utilizadas:**
    ```bash
    pip install -r requirements.txt
    ```

# Resultados
1. Separación de Datos
Se utilizaron tres conjuntos:

Entrenamiento (Train): 60% de los datos 
Validación (Validation): 20% de los datos
Prueba (Test): 20% de los datos

2. Resultados de los Modelos
#### KNN sin Framework (k=9)

| Métrica                | Train   | Validation | Test   |
|------------------------|---------|------------|--------|
| R-squared score        | 0.319   | 0.068      | 0.277  |
| Mean Absolute Error    | 0.498   | 0.597      | 0.628  |
| Mean Squared Error     | 0.410   | 0.579      | 0.621  |
| Root Mean Squared      | 0.640   | 0.761      | 0.788  |

#### KNN con Sklearn (k=9)

| Métrica                | Train   | Validation | Test   |
|------------------------|---------|------------|--------|
| R-squared score        | 0.295   | -0.011     | 0.242  |
| Mean Absolute Error    | 0.511   | 0.631      | 0.637  |
| Mean Squared Error     | 0.424   | 0.629      | 0.651  |
| Root Mean Squared      | 0.652   | 0.793      | 0.807  |

Sesgo y Varianza:

El sesgo es alto cuando el modelo no aprende la relación subyacente ni siquiera en el entrenamiento.
Aquí R² entrenando es solo 0.319 (muy por debajo de 1), MAE ~0.5 (alto).
Sesgo medio

Nivel de Ajuste (Fit):

La varianza es alta cuando hay mucha diferencia entre train y valid/test.
Aquí:

R² train = 0.319

R² val = 0.068 (gran caída)

MAE sube de 0.498 a 0.597/0.628
Predomina underfitting (no logra capturar bien el patrón ni siquiera en train), pero también se ve cierta varianza (la caída a 0.07 en validación).

Regularización:

Este modelo para estos datos vemos que estan haciendo un underfitting de los datos, por lo que cambiar a un modelo de clasificacion o incluso modelos mas como arboles mas complejos que nos puedan dar un mejor rendimiento y hacer cross validation para encontrar los mejores parametros en estos

## Conclusion
Este modelo es muy malo para este dataset, ya que los resultados vemos que tienen mucha varianza y underfitting, por lo que explorar modelos mas complejos puede ser la respuesta a tener una gran calidad de modelo

### Ejemplo de mejora
Al probar todos los k posibles el k=9 es el mejor con el r^2 mas alto para el test, pero sigue siendo muy bajo, por lo que cambiar a un modelo mas complejo posiblemente nos ayude a esto
cambiando el K de 12 a 9 vemos el cambio de r^2 fue de 0.20 a la tabla que tenemos arriba, por lo que elegir el k correcto es primordial en este modelo
se podria agregar futuramente en el modelo sin framework la regularizacion pero como primera iteracion no se tiene

**Recomendaciones adicionales:**
- Probar normalización de variables para mejorar la distancia entre vecinos.
- Usar validación cruzada para seleccionar el mejor valor de `k`.
- Documentar los cambios en las métricas tras cada ajuste para evidenciar la mejora.
