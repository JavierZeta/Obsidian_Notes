v serán las causas, el conocimiento que no tenga una dinámica temporal intrínseca

x será la que tenga esta dinámica temporal, se preocupa de que sea coherente a lo largo del tiempo

Necesito entender mejor x y v,   g y f.

$$
% 1. Definición de Errores de Predicción
\xi_v^{(i)} = \Pi_v^{(i)} \epsilon_v^{(i)} = \Pi_v^{(i)} (\mu_v^{(i-1)} - g(\mu^{(i)})) 
$$ $$
\xi_x^{(i)} = \Pi_x^{(i)} \epsilon_x^{(i)} = \Pi_x^{(i)} (D\mu_x^{(i)} - f(\mu^{(i)}))
$$


Estas primeras dos fórmulas calculan el error relativo, es decir, el error real (Diferencia entre el estado que había sido predicho anteriormente menos en el que se encuentra ahora) por la precisión


$$
% 2. Actualización de Estados (Inferencia)
\dot{\mu}_v^{(i)} = D\mu_v^{(i)} - (\partial_v \epsilon^{(i)})^T \xi^{(i)} - \xi_v^{(i+1)} $$$$
\dot{\mu}_x^{(i)} = D\mu_x^{(i)} - (\partial_x \epsilon^{(i)})^T \xi^{(i)}
$$ 


En esta fórmula se calcula la velocidad de variación de nuestro estado actual, la perfección se alcanza cuando es igual a 0.
Dμ es la inercia del cerebro de cambiar su estado, 
el siguiente cambia el estado en relación a cuanto cambia el error cambiando su estado y el valor del error relativo recibidio.

el último involucra a los errores de los estados anteriores.




$$
% 3. Plasticidad Sináptica (Aprendizaje)
\dot{\mu}_{\theta_{ij}} = -\partial_{\theta_{ij}} \epsilon^T \xi
$$
Esta fórmula explica como varían los parámetros de nuestras neuronas, como cambían las interconexiones entre ellas a largo plazo, y estas relacionadas con el error recibido.

$$

% 4. Ganancia Sináptica (Atención)
\dot{\mu}_{\gamma_i} = \frac{1}{2} tr \left( \partial_{\gamma_i} \Pi (\xi \xi^T - \Pi^{-1}) \right)$$

γ nos mide la sensibilidad que tendrán las neuronas, es decir, la cantidad de atención que pondremos a algo, y se medirá con respecto a la diferencia entre el error y la precisión, de forma que nos limpie todo el error producido por el ruido. 

