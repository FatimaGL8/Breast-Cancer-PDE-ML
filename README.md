# breast-cancer-pde-ml
### Resultados y análisis de simulaciones del cáncer de mama

El modelo completo considerado viene dado por el siguiente sistema de ecuaciones en derivadas parciales (EDP):

$$
\left\{
\begin{aligned}
\partial_t c - \nabla \cdot \left(D(x)\nabla c\right)
&=
a\, c \ln\left(\frac{K}{c}\right) - \gamma c \beta
&& \text{en } Q,
\\[8pt]
\partial_t \beta - \mu \Delta \beta
&=
-\delta \beta + u(t)
&& \text{en } Q,
\end{aligned}
\right.
$$

### Condiciones de Contorno e Iniciales

$$
\begin{aligned}
\frac{\partial c}{\partial n} = 0,
\qquad
\frac{\partial \beta}{\partial n} = 0
\quad &\text{en } \partial\Omega \times (0,T),
\\[8pt]
c(x,0)=c_0(x),
\qquad
\beta(x,0)=\beta_0(x)
\quad &\text{en } \Omega.
\end{aligned}
$$

### Descripción de Variables y Parámetros

| Símbolo | Descripción |
| :---: | :--- |
| $c(x,t)$ | Densidad de células tumorales |
| $\beta(x,t)$ | Concentración del fármaco |
| $D(x)$ | Coeficiente de difusión celular (espacialmente dependiente) |
| $a$ | Tasa de proliferación tumoral |
| $K$ | Capacidad de carga del tejido (crecimiento Gompertziano) |
| $\gamma$ | Eficacia del tratamiento (tasa de muerte celular por fármaco) |
| $\mu$ | Coeficiente de difusión del medicamento |
| $\delta$ | Tasa de degradación/eliminación del fármaco |
| $u(t)$ | Dosificación o administración externa de quimioterapia |
