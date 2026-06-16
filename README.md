# 🔬📊 Resultados y análisis de simulaciones del cáncer de mama 🎗️

## 📖 Descripción
En este repositorio se presentan los principales resultados obtenidos a partir de la implementación computacional del modelo matemático desarrollado para la simulación del crecimiento del cáncer de mama.

El objetivo principal consiste en analizar el comportamiento dinámico del sistema bajo distintos escenarios terapéuticos, estudiar la influencia de los parámetros biológicos y evaluar la capacidad descriptiva del modelo desde un punto de vista matemático, numérico y computacional.

---

## 📐 Modelo Matemático Completo (EDP)

El modelo completo considerado viene dado por el siguiente sistema de ecuaciones en derivadas parciales (EDP):

$$
\begin{cases}
\partial_t c - \nabla \cdot (D(x)\nabla c) = a c \ln\left(\frac{K}{c}\right) - \gamma c \beta & \text{en } Q, \\
\partial_t \beta - \mu \Delta \beta = -\delta \beta + u(t) & \text{en } Q.
\end{cases}
$$

### 📋 Condiciones de Contorno e Iniciales

$$
\begin{aligned}
\frac{\partial c}{\partial n} = 0, \quad \frac{\partial \beta}{\partial n} = 0 & \quad \text{en } \partial\Omega \times (0,T), \\
c(x,0)=c_0(x), \quad \beta(x,0)=\beta_0(x) & \quad \text{en } \Omega.
\end{aligned}
$$

<details>
<summary><b>🔍 Ver descripción de variables y parámetros</b></summary>
<br>

* **$c(x,t)$**: Representa la densidad de células tumorales.
* **$\beta(x,t)$**: Corresponde a la concentración del fármaco.
* **$D(x)$**: Es el coeficiente de difusión celular.
* **$a$**: Es la tasa de proliferación tumoral.
* **$K$**: Es la capacidad de carga.
* **$\gamma$**: Mide la eficacia del tratamiento.
* **$\mu$**: Representa la difusión del medicamento.
* **$\delta$**: Modela la degradación del fármaco.
* **$u(t)$**: Describe la administración externa de quimioterapia.
</details>

---

## 🗂️ ¿Qué incluye este repositorio?

### ⚙️ 1. Solución del Problema Directo (Métodos Numéricos)
Pipeline en Python para la resolución temporal a largo plazo del sistema acoplado utilizando esquemas explícitos de **Diferencias Finitas** sobre mallas uniformes bidimensionales $100 \times 100$, parametrizados bajo el cumplimiento estricto de la condición de estabilidad de Courant-Friedrichs-Lewy (CFL).

### 🎯 2. Análisis de Sensibilidad y Optimización Dosis-Respuesta
Herramientas computacionales para el estudio estructural del modelo a través de barridos multivariantes discretos y continuos, monitorizando la masa tumoral integrada:
$$M(t) = \iint_{\Omega} c(x,y,t) \,dx\,dy$$

### 🧠⚡ 3. Solución del Problema Inverso (FNN + PINN)
Un framework híbrido de aprendizaje profundo diseñado para la estimación de parámetros biológicos inobservables y el filtrado de ruido estocástico clínico:
* **FNN Morfológica (Data-Driven):** Red densa que procesa datos de biopsias para predecir un índice exógeno de malignidad $\alpha \in [0,1]$.
* **PINN Acoplada (Physics-Informed):** Red neuronal cuyo funcional de pérdida multiobjetivo está regularizado por los residuos analíticos de la EDP ($r_c$), evaluados mediante diferenciación automática (AD) y protegida contra indeterminaciones (*NaN*) mediante operadores *Softplus* modificados.

---

## 🗺️ Hoja de Ruta de Experimentos Numéricos

Las simulaciones realizadas permiten estudiar la evolución espacio-temporal de la densidad tumoral, la propagación del agente quimioterapéutico y la interacción entre proliferación celular, difusión e inhibición terapéutica a través de los siguientes bloques:

| Bloque de Simulación | Enfoque Principal |
| :--- | :--- |
| **01. Control y Validación** | Evolución tumoral basal (sin tratamiento quimioterapéutico). | 
| **02. Terapia Continua** | Simulación del Modelo Completo vs. Modelo Simplificado (Concentración constante $\beta_0$). | 
| **03. Optimización de Dosis** | Análisis del impacto de la intensidad terapéutica en la regresión tumoral. |
| **04. Robustez del Modelo** | Análisis de sensibilidad paramétrica multivariante (parámetros $a$, $K$ y $\gamma$). | 
| **05. IA y Parámetros** | Estimación avanzada de parámetros biomédicos latentes mediante Redes Neuronales *Feedforward* (FNN) y PINNs. | 

---

## 📂 Desglose de Resultados por Subsección

<details>
<summary><b>🔹 1. Validación numérica del modelo y evolución tumoral sin tratamiento</b></summary>
<br>

Estudio de la evolución espacio-temporal de la densidad tumoral en su escenario basal (historia natural de la enfermedad). Valida la consistencia biológica del crecimiento Gompertziano y la difusión libre bajo condiciones de contorno de Neumann homogéneas antes de aplicar perturbaciones terapéuticas.
</details>

<details>
<summary><b>🔹 2. Simulación con tratamiento quimioterapéutico continuo: Modelo Completo</b></summary>
<br>

Modelado acoplado de la interacción dinámica entre el transporte difusivo del agente quimioterapéutico, su aclaramiento metabólico y la inhibición celular citotóxica.
* *Sub-análisis:* **Modelo simplificado con concentración constante de fármaco** (análisis comparativo que demuestra el impacto de los tiempos de latencia y difusión frente a una perfusión idealizada).
</details>

<details>
<summary><b>🔹 3. Influencia de la intensidad terapéutica</b></summary>
<br>

Evaluación dosis-respuesta mediante el análisis de sensibilidad discreto de la carga farmacológica. Identifica los diferentes regímenes dinámicos del sistema (crecimiento, estabilización crónica y regresión parcial) y valida matemáticamente la ley de los rendimientos marginales decrecientes a través del índice de eficacia relativa $E(\beta)$.
</details>

<details>
<summary><b>🔹 4. Análisis de sensibilidad paramétrica</b></summary>
<br>

Estudio multivariante del impacto marginal de las fluctuaciones en los parámetros biológicos críticos ($a$, $K$ y $\gamma$) sobre la masa tumoral integrada a largo plazo, garantizando la robustez estructural, la estabilidad y la alta capacidad descriptiva del modelo matemático de reacción-difusión.
</details>

<details>
<summary><b>💡 5. Estimación de parámetros mediante redes neuronales y PINNs</b></summary>
<br>

Resolución del problema inverso no lineal mediante el acoplamiento de una FNN morfológica y una red neuronal informada por la física (PINN). El modelo se nutre del [Wisconsin Breast Cancer Dataset (Descargar archivo .zip)](./data/breast+cancer+wisconsin+diagnostic.zip) para extraer las variables geométricas macroscópicas de los pacientes. A partir de estos flujos y de datos espacio-temporales con ruido, el framework filtra las perturbaciones estocásticas y reconstruye los campos continuos de densidad celular, identificando con alta precisión matemática los parámetros biomédicos latentes de forma estrictamente personalizada.
</details>

---

## 🔍 ¿Qué encontrarás aquí?
* **Modelos directos validados:** Scripts en Python que reproducen dinámicas de crecimiento y regresión estables sin introducir difusión numérica artificial.
* **Framework de inversión robusto:** Arquitecturas neuronales que asimilan pérdidas no convexas, equilibrando las restricciones físicas con datos experimentales con ruido.
* **Clasificadores clínicos de soporte:** Modelos estadísticos de validación macroscópica complementaria (Regresión Logística estratificada) con una precisión (*Accuracy*) demostrada del $96.49\%$.
* **Visualizaciones y reproducibilidad:** Gráficos dosis-respuesta, diagramas de dispersión de ajuste continuo y curvas de evolución paramétrica asintótica.

---

## 📚 Bibliografía (Evolución del Proyecto)
o Guijarro-López, F. (2025). *Neural-Network-Based-Solutions-to-Differential-Equations*. [Enlace](https://github.com/FatimaGL8/Neural-Network-Based-Solutions-to-Differential-Equations). GitHub.
o Fife, P. C. (1979). *Reaction-Diffusion Equations and Their Applications to Biology*. Springer.
o LeVeque, R. J. (2007). *Finite Difference Methods for Ordinary and Partial Differential Equations*. SIAM.
o Strauss. W. A. (2007) *Partial Differential Equations: An Introduction*. Wiley, (edition 2).
o Python Software Foundation. [*PYTHON*.](https://www.python.org/)
o PyTorch documentation. [*PYTORCH*.](https://pytorch.org/)
o TensorFlow documentation. [*TENSORFLOW*.](https://www.tensorflow.org/)
o NumPy documentation. [*NUMPY*.](https://numpy.org/)
* **UCI Machine Learning Repository (2024).** *Breast Cancer Wisconsin (Diagnostic) Data Set*. [Enlace al dataset de la UCI](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic).
