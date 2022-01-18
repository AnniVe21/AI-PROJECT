# PORTAFOLIO
### Inteligencia Artificial y Aprendizaje reforzado

*   Natalia Castilla Reyes - ancastillar@unal.edu.co
*   Miguel Angel Medina Rangel - mamedinar@unal.edu.co 
*   Anni Melissa Velandia Echeverry - avelandiae@unal.edu.co

La gestión de carteras es un problema financiero en el que un agente redistribuye constantemente algún recurso financiero en un conjunto de activos con el fin de maximizar el rendimiento. Para este proyecto se proponé aplicar la metodología de aprendizaje de reforzado profundo al problema, con la ayuda de una Recurrent Neural Red (RNN) aplicada en el historico de las acciones de las empresas más representativas del mercado de valores Colombiano.

```math
SE = \frac{\sigma}{\sqrt{n}}
```

# Problematica

Se proponé aplicar la metodología de aprendizaje de reforzado profundo aprendida en clase, con la ayuda de una Recurrent Neural Red (RNN), con el objetivo de crear **un agente que administre y gestione de manera optimá y lucrativa un portafolio diario de acciones de las empresas más representativas del mercado de valores Colombiano** como lo son Grupo Aval, Grupo Bolivar, Grupo Antioqueño, Ecopetrol, entre otros.

# Supuestos

* Continuidad: El precio de cierre de alguna acción específica, en el tiempo $t$, es el precio de apertuta en el instante $t+1$
* Impacto insignificante en el mercado: Los precios de las acciones se dan como datos de entrada y no deben verse afectados por las acciones del agente.
* Unidad de acciones: En lugar de un número de acciones discreto, se permite que el agente pueda negociar cantidades continuas de acciones (por ejemplo, 3.4 acciones).


# Definiciones:

**Portafolio:** Un portafolio es un subconjunto de $L$ acciones que pertenecen a un conjunto de $M^k$ activos totales presentes en el periodo $k$, por ejemplo: un portafolio puede estar compuesto por $0.3*Ecopetrol+0.5*BBVA+0.2*Dav$, debemos tener en cueta que tenemos la restricción: 
$$ \sum_i p_i =1$$

Donde $p_i$ corresponde al peso de la acción en un determinado portafolio


**Estado:** Considere el histórico de precios de un total de $L$ acciones, donde el histórico de precios para un momento $k$, viene dado por:

$$ S^k =(S_1^k,..., S_L^k) $$

Note, que se está tomando el paso de tiempo de manera discreta. 

Por otra parte se define el portafolio para el estado de las acciones en el tiempo $k$, como:

$$ P^k = (P_1^k,..., P_L^k ), \quad \sum_{i=1}^LP_i=1$$

Cada $P_i$ corresponde al procentaje de determinada acción en el portafolio. Con las definiciones anteriores podemos definir el estado de la siguiente manera:

 $$ Estado^k = (S^{k-N},S^{k-N+1},..., S^{k-1}, S^k, P^{k-1} ) $$

Donde $N$ es la ventana de tiempo definida para los estados y el desarrollo de la RNN

 **Acciones:**

 Las acciones se definen como la cartera $P_k$ que se elige en cada paso de tiempo, de acuerdo con $ P^k = (P_1^k,..., P_L^k )$, donde cada porcentaje $P_j^k$ se maneja en un espacio continuo de suma 1 (similar al ejemplo del bandido multibrazo).

**Recompensa:**

Se define la recompensa $((S^{k-N},S^{k-N+1},..., S^{k-1}, S^k, P^{k-1} ),P^k)$ como el retorno de la inversión en la siguiente cartera $P^k$, donde el rendimiento esta determinado por la ganancia correspondiente al cambio porcentual entre el precio del estado $k+1$ con respecto al estado $k$ ponderado para cada uno de los activos que componen el portafilo con su respectivo $P^k$:
$$r^k=\sum_{i=1}^L\frac{M^kP_i^k}{S_i^k}(S_i^{k+1}-S_i^k)$$

**Politica:**

Para la metodología de aprendizaje de reforzado, se utilizan redes neuronales profundas (RNN) como política del agente, donde dados los estados se usa el modelo de red para extraer características y dar las acciones correspondientes.



# Bibliografia

* CS221 Project Final Report Deep Reinforcement Learning in Portfolio Management, Zhan.R & Tianchang.He,  2019
* Modern Invest Theory, Robert A. Haugen, Prentice Hall, 1986
* Online portfolio selection: A survey, Bin Li and Steven CH Hoi, ACM Computing Serveys (CSUR), 46(3):35,
2014

