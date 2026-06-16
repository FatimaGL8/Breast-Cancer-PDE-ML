## 🔬📊 Resultados y análisis de simulaciones del cáncer de mama 🎗️

En este repositorio se presentan los principales resultados obtenidos a partir de la implementación computacional del modelo matemático desarrollado para la simulación del crecimiento del cáncer de mama.

El objetivo principal consiste en analizar el comportamiento dinámico del sistema bajo distintos escenarios terapéuticos, estudiar la influencia de los parámetros biológicos y evaluar la capacidad descriptiva del modelo desde un punto de vista matemático, numérico y computacional.

---

### 📐 Modelo Matemático Completo (EDP)

El modelo completo considerado viene dado por el siguiente sistema de ecuaciones en derivadas parciales (EDP):

$$
\begin{cases}
\partial_t c - \nabla \cdot (D(x)\nabla c) = a c \ln\left(\frac{K}{c}\right) - \gamma c \beta & \text{en } Q, \\
\partial_t \beta - \mu \Delta \beta = -\delta \beta + u(t) & \text{en } Q.
\end{cases}
$$

#### 📋 Condiciones de Contorno e Iniciales

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

### 🗺️ Hoja de Ruta de Experimentos Numéricos

Las simulaciones realizadas permiten estudiar la evolución espacio-temporal de la densidad tumoral, la propagación del agente quimioterapéutico y la interacción entre proliferación celular, difusión e inhibición terapéutica a través de los siguientes bloques:

| Bloque de Simulación | Enfoque Principal |
| :--- | :--- |
| **01. Control y Validación** | Evolución tumoral basal (sin tratamiento quimioterapéutico). | 
| **02. Terapia Continua** | Simulación del Modelo Completo vs. Modelo Simplificado (Concentración constante $\beta_0$). | 
| **03. Optimización de Dosis** | Análisis del impacto de la intensidad terapéutica en la regresión tumoral. |
| **04. Robustez del Modelo** | Análisis de sensibilidad paramétrica multivariante (parámetros $a$, $K$ y $\gamma$). | 
| **05. IA y Parámetros** | Estimación avanzada de parámetros biomédicos latentes mediante Redes Neuronales *Feedforward* (FNN) y PINNs. | 

---

### 📂 Desglose de Resultados por Subsección

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
