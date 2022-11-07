# Logistic_Humanitarian
## Optimization Model
### Conjuntos

$D$ : Conjunto de distritos

$E$ : Conjunto de distritos prioritarios $E \subset D$, este conjunto de distritos deben ser atendidos bajo el criterio de calidad de servicio predefinido. 

$I$ : Conjunto de albergues




### Parámetros 

$r_d$ = Distancia mínima entre el distrito $d \in D$ y la costa (Dicho parámetro puede ser considerado como altura o profundidad en caso de tsunami) 

$T_{id}$ = Tiempo mínimo necesario de traslado entre el distrito $d \in D$ y el albergue $i \in I$ 

$\delta_{id}$ = Disminución de los tiempos mínimos requeridos a la conexión entre el distrito $d \in D$ y el albergue $i \in I$ producto de la inversión. 

$C_q, C_h$ = Costos unitarios asociados a la cantidad de personas en el distrito y la altura en metros respectivamente. 

$H_d^{min}$ = Altura mínima necesaria (en metros) en caso de construir un albergue vertical $i \in I$ en el distrito $d \in D$. 

$p_d$ = Población flotante estimada según el distrito $d \in D$. 

$C_{id}$ = Inversión total para crear o mejorar la conexión de carreteras entre el distrito $d \in D$ y el albergue vertical $i \in I$

$T^{max}$ = Tiempo máximo de traslado establecido por las autoridades. 

### Variables 

$y_i$ = 1, si se selecciona el albergue $i \in I$, 0 si no. 

$z_{id}$ = 1, si invierta en la conexión de ruta entre el distrito $d \in D$ hacia el albergue $i \in I$

$f_{id}$ = proporción de inversión en la conexión de ruta entre el distrito $d \in D$ hacia el albergue $i \in I$

$q_i$ = capacidad que deberá tener el albergue $i \in I$ en caso de abrirse e invertir en el.

$h_i$ = altura que deberá tener el albergue $i \in I$ en caso de abrirse e invertir en el. 

$\tau_{id}$ = Tiempo mejorado mínimo necesario de traslado desde el distrito $d \in D$ hacia el albergue $i \in I$


\begin{align}
    %Funciíon Obj
    Min Z = (f_1,-f_2,f_3) && (1)\\
    \\
    % Min. Tiempos de origen-destino
    f_1 = \sum_{i \in I}\$C^hh_i+\sum_{i \in I}\$C^qq_i+\sum_{i \in I}\sum_{d \in D}\$C_{id}f_{id} && (2)\\ \\
    f_2 = \sum_{i \in I}\sum_{d \in D}(p_d+p_i)(r_i-r_d)z_{id} && (3)\\ \\
    f_3 = \sum_{i \in I}\sum_{d \in D}\tau_{id}z_{id} && (4)
\end{align}

s.t.
\begin{align}
    \sum_{i \in I}z_{id} = 1 && \forall d \in E && (5)\\ \\
    z_{id}-y_i \leq 0 && \forall i \in I, d \in D && (6)\\ \\
    z_{id}-y_i = 0 && \forall i \in I, d \in D, i=d && (7)\\ \\
    f_{id}-z_{id} \leq 0 && \forall i \in I, d \in D && (8)\\ \\
    T_{id}-f_{id}\delta_{id} \leq \tau_{id} && \forall i \in I, d \in D && (9)\\ \\
    \sum_{d \in D}z_{id}p_d-q_i \leq 0 && \forall i \in I, y_i = 1 && (10)\\ \\
    h_i-H_d^{min}y_i \geq 0 && \forall i \in I && (11)\\ \\
    \tau_{id}z_{id} \leq T^{max} && \forall i \in I, d \in D && (12)\\ \\
    (r_i-r_d)z_{id} \geq 0 && \forall i \in I, d \in D && (13) \\ \\
    y_i+y_d = 1 && \forall i \in I, d \in D, z_{id}=1, i \neq d && (14) \\ \\
    \sum_{i \in I}z_{id} \leq 1 && \forall d \in D && (15)
\end{align}
