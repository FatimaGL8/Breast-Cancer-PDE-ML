## 🔬📊 Resultados y análisis de simulaciones del cáncer de mama 🎗️

En esta sección se presentan los principales resultados obtenidos a partir de la implementación computacional del modelo matemático desarrollado para la simulación del crecimiento del cáncer de mama. 

El objetivo principal consiste en analizar el comportamiento dinámico del sistema bajo distintos escenarios terapéuticos, estudiar la influencia de los parámetros biológicos y evaluar la capacidad descriptiva del modelo desde un punto de vista matemático, numérico y computacional.

---

### 📐 Marco Matemático: Modelo Completo (EDP)

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

| Bloque de Simulación | Enfoque Principal | Estado / Estatus |
| :--- | :--- | :---: |
| **01. Control y Validación** | Evolución tumoral basal (sin tratamiento quimioterapéutico). | 🟩 Completado |
| **02. Terapia Continua** | Simulación del Modelo Completo vs. Modelo Simplificado ($C = cte$). | 🟩 Completado |
| **03. Optimización de Dosis** | Análisis del impacto de la intensidad terapéutica en la regresión. | 🟩 Completado |
| **04. Robustez del Modelo** | Análisis de sensibilidad paramétrica global. | 🟩 Completado |
| **05. IA y Parámetros** | Estimación avanzada mediante Redes Neuronales y PINNs. | 🚀 Destacado |

---

### 📂 Desglose de Resultados por Subsección

<details>
<summary><b>🔹 1. Validación numérica del modelo y evolución tumoral sin tratamiento</b></summary>
<br>

Estudio de la evolución espacio-temporal de la densidad tumoral de forma basal. Permite identificar la tasa de proliferación natural y los patrones de difusión libre del tejido tumoral antes de aplicar perturbaciones externas.
</details>

<details>
<summary><b>🔹 2. Simulación con tratamiento quimioterapéutico continuo: Modelo Completo</b></summary>
<br>

Modelado de la interacción dinámica entre la propagación del agente quimioterapéutico y la inhibición celular.
* *Sub-análisis:* **Modelo simplificado con concentración constante de fármaco** (análisis comparativo de coste computacional y precisión).
</details>

<details>
<summary><b>🔹 3. Influencia de la intensidad terapéutica</b></summary>
<br>

Asimismo, los experimentos numéricos permiten identificar distintos regímenes dinámicos del sistema, incluyendo crecimiento tumoral, estabilización y procesos de regresión parcial inducidos por el tratamiento a través de la variación de la dosis.
</details>

<details>
<summary><b>🔹 4. Análisis de sensibilidad paramétrica</b></summary>
<br>

Estudio del impacto de las fluctuaciones en los parámetros biológicos sobre las soluciones numéricas, garantizando la robustez y la capacidad descriptiva del modelo de reacción-difusión para reproducir dinámicas coherentes con la oncología matemática clásica.
</details>

<details>
<summary><b>💡 5. Estimación de parámetros mediante redes neuronales y PINNs</b></summary>
<br>

Uso de técnicas de aprendizaje profundo e *Physics-Informed Neural Networks* (PINNs) para la resolución de problemas inversos. Permite validar cualitativamente el comportamiento del modelo, ajustando y estimando los parámetros biológicos críticos a partir de datos simulados.
</details>
