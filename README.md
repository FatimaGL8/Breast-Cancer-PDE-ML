# breast-cancer-pde-ml
### Resultados y análisis de simulaciones del cáncer de mama

El modelo completo considerado viene dado por el siguiente sistema de ecuaciones en derivadas parciales (EDP):

$$
\begin{cases}
\partial_t c - \nabla \cdot (D(x)\nabla c) = a c \ln\left(\frac{K}{c}\right) - \gamma c \beta & \text{en } Q, \\
\partial_t \beta - \mu \Delta \beta = -\delta \beta + u(t) & \text{en } Q.
\end{cases}
$$

### Condiciones de Contorno e Iniciales

$$
\begin{aligned}
\frac{\partial c}{\partial n} = 0, \quad \frac{\partial \beta}{\partial n} = 0 & \quad \text{en } \partial\Omega \times (0,T), \\
c(x,0)=c_0(x), \quad \beta(x,0)=\beta_0(x) & \quad \text{en } \Omega.
\end{aligned}
$$

### Descripción de Variables y Parámetros

- $c(x,t)$ representa la densidad de células tumorales,
- $\beta(x,t)$ corresponde a la concentración del fármaco,
- $D(x)$ es el coeficiente de difusión celular,
- $a$ es la tasa de proliferación tumoral,
- $K$ es la capacidad de carga,
- $\gamma$ mide la eficacia del tratamiento,
- $\mu$ representa la difusión del medicamento,
- $\delta$ modela la degradación del fármaco,
- y $u(t)$ describe la administración externa de quimioterapia.
