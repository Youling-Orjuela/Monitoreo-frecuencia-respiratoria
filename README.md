# Monitoreo del patrón y frecuencia respiratoria
## Introducción
La respiración es un proceso esencial que permite el intercambio de oxígeno y dióxido de carbono, logrando así garantizar la homeostasis. Desde el punto de vista de la ingeniería biomédica este proceso se puede analizar como un sistema dinámico representado por variables físicas que se pueden cuantificar, como lo es la presión, el volumen, el flujo, la frecuencia respiratoria y más. Todas estas variables permiten el desarrollo de modelos cuantitativos del sistema respiratorio [1].


Según varias investigaciones se ha demostrado que la frecuencia respiratoria es uno de los signos vitales más sensibles para detectar y preventir eventos graves, como el paro cardiopulmonar [2][3][4]. Por esta razón, es importante comprender todas las variables involucradas en el proceso respiratorio y saber que sensores existen que sean ideales para medir cada una de estas variables, para llegar a tener la mejor caracterización de la frecuencia respiratoria.

## Variables físicas
En el proceso respiratorio intervienen varias variables físicas que describen cómo es el mecanismo en el cual, el aire entra a los pulmones, para un posterior intercambio de gases y una regulación por parte del organismo de ese proceso [5][6]. Entre las variables de índole mecánica se encuentra el volumen pulmonar, que representa la cantidad de aire que contienen los pulmones en las múltiples fases de la respiración y depende del movimiento de la caja torácica y del diafragma [5]; la presión respiratoria, la cual es considerada como la fuerza que impulsa el aire hacia dentro o fuera de los pulmones y se da gracias a los cambios de volumen generados del tórax [6]; y el flujo de aire, que indica la rapidez con la que el aire se desplaza a través de las vías respiratorias como consecuencia de los gradientes de presión [7]. Relacionado a este flujo aparece la resistencia de las vías aéreas, que depende del diámetro de los bronquios y bronquiolos y determina la facilidad, o en su defecto la dificultad, de circulación del aire [6][7]. También destaca la compliancia pulmonar, que refleja la capacidad del pulmón y del tórax para expandirse al afrontar un cambio de presión y se relaciona con la elasticidad del tejido pulmonar [5][8].

Durante el intercambio gaseoso hay intervención de variables como la presión parcial de los gases, principalmente oxígeno y dióxido de carbono, variable que expresa la tendencia de cada gas a difundirse desde los alvéolos hacia la sangre o viceversa [6][8]; la fracción de gas inspirado, cuya función es indicar la proporción de oxígeno presente en el aire inhalado [5]; y la capacidad de difusión, que depende del área de intercambio alveolar, del grosor de la membrana respiratoria y del gradiente de presión entre alvéolo y capilar [6][8]. Una vez en la sangre, se consideran variables como la saturación de oxígeno y el flujo sanguíneo pulmonar, las cuales permiten evaluar la eficiencia del transporte de oxígeno hacia los tejidos [5][7].

Adicionalmente, el proceso respiratorio está influido por variables ambientales y temporales, tales como la temperatura y la humedad del aire inspirado, las cuales determinan el acondicionamiento del aire en las vías respiratorias [6]. Por otro lado, la frecuencia respiratoria y los tiempos de inspiración y espiración, tomadas como variables temporales, describen el ritmo con el que se repite el ciclo respiratorio y dependen del control neural y químico del sistema respiratorio [5][8]. Gracias a este factor temporal, se puede determinar la periodicidad o la frecuencia del proceso respiratorio, conociendo datos como la cantidad de respiraciones por minuto y así lograr una estimación de la salud respiratoria de la persona [7][1].

La suma de estas variables, y otras más que se han analizado en múltiples estudios, permiten comprender la respiración como un fenómeno físico y fisiológico integrado, fundamental para el mantenimiento del equilibrio y el correcto funcionamiento del organismo [5][6].


## Sensor a emplear
En el proceso respiratorio, una de las variables físicas de mayor relevancia es la expulsión de dióxido de carbono de los pulmones en la fase de exhalación. La concentración del CO2 en el aire exhalado presenta un comportamiento periódico, directamente asociado al ciclo respiratorio de la persona, lo que permite utilizarla como una variable indirecta para la determinación de la frecuencia respiratoria, gracias a su comportamiento cíclico. En cada espiración se genera un incremento temporal en la concentración de CO2, mientras que durante la inspiración dicha concentración decrece, dando lugar a una señal oscilatoria que puede ser analizada tanto en el dominio del tiempo, como en el dominio de la frecuencia y así dar lugar a la cantidad de respiraciones por minuto.

Para la adquisición de esta variable; y derivado de esto calcular la frecuencia respiratoria, se hace uso de un sensor de gas "MQ-3", cuya respuesta se da en las variaciones en la concentración de gases presentes en el aire exhalado. Aunque el MQ-3 es comúnmente utilizado para la detección de alcohol, su principio de funcionamiento fundamentados en las variaciones de resistencia del material sensor frente a los gases reductores, permite detectar variaciones relativas en la composición del aire exhalado por el usuario. Al adaptar el sensor cerca de la vía respiratoria, es posible registrar una mayor concentración de CO2 en la fase espiratoria de cada respiracion, con el fin de determinar la frecuencia respiratoria del usuario de una manera no invasiva.

El sensor de gas MQ-3 es un sensor semiconductor de óxido metálico (MOS) que puede detetar variaciones en la composición del aire, esto lo hace  midiendo los cambios en la resistencia eléctrica. La parte más sensible del sensor esta recubierta de óxido de estaño (SnO₂) y se mantiene calentado internamente para facilitar las reacciones quimicas con los gases involucrados. En aire limpio, el oxígeno se adhiere en la superficie del material, atrayendo a los electrones del mismo y aumentando la resistencia; cuando hay gases reductores como el alcohol o compuestos del aire exhalado, estas moléculas reaccionan con el oxígeno , liberando electrones y disminuyendo la resistencia del sensor. La variación de resistencia genera una señal eléctrica proporcional a la cantidad de gas detectado y puede leerse como un voltaje analógico o digital que detecta cambios cíclicos en la composición del aire [9].

## Adquisición de la señal
Aún hace falta
## Resultados obtenidos
No tenemos resultados todavía 
## Análisis y conclusiones
• Análisis 1: Determine semejanzas y diferencias (si las hay) entre la
frecuencia y relación entre inhalaciones y exhalaciones de un individuo
sano bajo condiciones de reposo y durante tareas de verbalización.
• Análisis 2: Evalúe el alcance y las posibles limitaciones de emplear el
sistema construido durante la práctica para detectar patologías en seres
humanos.


Pregunta 1: ¿Son los patrones respiratorios y frecuencias respiratorias
iguales o diferentes en cada caso? ¿A qué se debe esto?
• Pregunta 2: ¿Cuáles serían las ventajas y desventajas de emplear múltiples
sensores para el monitoreo del proceso respiratorio? ¿Cuáles podrían ser
las razones?

## Bibliografía
[1] J. D. Bronzino and D. R. Peterson, Biomedical Engineering Fundamentals.
    Boca Raton, FL: CRC Press, 2006. doi:10.1201/9781420003857.

[2] J. F. Fieselmann et al., “Respiratory rate predicts cardiopulmonary arrest
    for internal medicine inpatients,” J. Gen. Intern. Med., 1993.

[3] C. P. Subbe et al., “Effect of introducing the Modified Early Warning Score…,”
    Anaesthesia, 2003.

[4] D. R. Goldhill et al., “A physiologically-based early warning score…,”
    Anaesthesia, 2005.
    
[5] Guyton, A. C., & Hall, J. E. Textbook of Medical Physiology. Elsevier.

[6] West, J. B. Respiratory Physiology: The Essentials. Lippincott Williams & Wilkins.

[7] Levitzky, M. G. Pulmonary Physiology. McGraw-Hill.

[8] Ganong, W. F. Review of Medical Physiology. McGraw-Hill.

[9] S. Prabhu, “In-Depth: How MQ3 Alcohol Sensor Works? & Interface it with Arduino,” Last Minute Engineers, Jan. 20, 2026. https://lastminuteengineers.com/mq3-alcohol-sensor-arduino-tutorial
