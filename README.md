# Trabajo Práctico Grupal de Algoritmos y Programación II
 Primer Cuatrimestre 2025

## Ojbetivo

El objetivo de este trabajo es aplicar los conceptos aprendidos en clase en la resolución de un problema práctico, demostrando la capacidad de diseñar e implementar soluciones eficientes utilizando estructuras de datos y algoritmos avanzados.

## Enunciado

Desarrollar un **Sistema Integrado de Gestión de Operaciones Aeropuertarias** (SIGOA) que abarque la gestión de las operaciones de un aeropuerto, utilizando diversas estructuras de datos y técnicas algorítmicas para optimizar los procesos de check-in, gestión de carga y control de vuelos.

### Objetivos Específicos

- Diseñar e implementar un sistema que simule las operaciones de un aeropuerto, incluyendo el check-in de pasajeros, la gestión de carga y el despacho de vuelos.
- Utilizar estructuras de datos adecuadas (pilas, colas, listas, colas de prioridad, árboles binarios) para representar la información y gestionar los procesos.
- Aplicar algoritmos de búsqueda, ordenamiento y optimización para mejorar la eficiencia del sistema.
- Implementar técnicas de compresión de datos para el almacenamiento eficiente de la información del vuelo.
- Evaluar el rendimiento del sistema mediante pruebas con diferentes escenarios de tráfico aéreo y volumen de pasajeros/carga.
- Documentar el diseño, la implementación y los resultados del sistema en un informe técnico detallado.

### Descripción del Sistema

#### 1. Check-in de pasajeros

- Cada vuelo tiene un número de vuelo, una fecha y hora de salida programada, y una lista de pasajeros asignados y abre el check-in 2 horas antes de la salida del vuelo.
- Cada pasajero se identifica con su número de documento, que puede ser DNI o pasaporte. El sistema debe permitir buscar un pasajero y recuperar su número de reserva, nombre, apellido, categoría de pasajero (platino, oro o plata) y el número de vuelo al que está asignado. En una reserva pueden haber hasta 5 pasajeros.
- Los pasajeros llegan al aeropuerto y se dirigen a los mostradores de check-in. (Se debe simular la llegada de los pasajeros al aeropuerto y su espera en la cola de check-in). Se estima que cada pasajero tarda entre 1 y 5 minutos en realizar el check-in.
- Se implementa una única cola para gestionar la espera de los pasajeros en el mostrador de check-in y se pueden habilitar varios mostradores para atender a losº
- Los pasajeros pueden despachar su equipaje y recibir su tarjeta de embarque, siempre y cuando se encuentren en la lista de pasajeros del vuelo. 
- El sistema debe emitir un ticket de equipaje por cada bulto despachado, que contenga el número de vuelo, el número de documento del pasajero, el número de bultos despachados y el peso total del equipaje.
- El vuelo puede tener pasajeros en lista de espera. Cuando la aerolíneas cierra el proceso de check-in si hay asientos disponibles asigna esos a asientos a los pasajeros en lista de espera. La asignación se realiza por prioridad y por orden de llegada, así los pasajeros frecuentes de la categoría platino son los que tienen mayor prioridad, luego los de la categoría oro, y por último los de la categoría plata. Si hay pasajeros que no son pasajeros frecuentes, se asignan luego de todos los pasajeros frecuentes.

#### 2. Gestión de cargas

- Los aviones pueden transportar carga, la cual debe ser gestionada de manera eficiente. 
- Los paquetes de carga se encuentran en el aeropuerto, identificados por el destino, el peso y el volumen.
- Cada aeronave tiene una capacidad máxima de carga en peso y volumen, y se deben respetar estas restricciones al cargar los paquetes.
- Los paquetes se deben asignar tratando de maximizar el uso del espacio y respetando las restricciones de peso.
- La carga se realiza 2 hs antes de la salida del vuelo. Una vez finalizada se procede al embarque de los pasajeros

#### 3. Embarque de pasajeros
   
- Los pasajeros deben embarcar en el avión de acuerdo a un orden establecido.
- Los pasajeros de la categoría platino, oro y plata pueden embarcar en cualquier momento.
- Los pasajeros restantes embarcan por zonas, primero se habilita el embarque de la zona 1, luego la zona 2 y así sucesivamente. 
- Cada vuelo se divide en al menos dos zonas que se indican en la tarjeta de embarque. Los que tienen asientos asignados en la parte de atrás corresponden a la zona 1, los del medio a la zona 2 y los de adelante a la zona 3
- Una vez que todos los pasajeros han embarcado, se cierra la puerta del avión y el avión queda en estado listo para despegar. Esperando las instrucciones del control de tráfico aéreo.
- Llegada la hora límite, si algún pasajero no se presenta se lo da de baja de la nómina de pasajeros.
- Toda la información relativa al vuelo se registra en un archivo de texto, incluyendo el número de vuelo, la fecha y hora de salida programada, la fecha y hora de partida real, la lista de los pasajeros embarcados, la lista de bultos despachados en calidad de equipaje, la lista de los pasajeros que no se presentaron, la lista de los pasajeros en lista de espera, y la lista de los paquetes de carga embarcados. El archivo se comprime con el algoritmo código de Huffman y se almacena en el servidor del aeropuerto. 

#### 4. Despacho de vuelos

- Los vuelos deben ser despachados de acuerdo a un horario programado.
- Se implementa una cola de prioridad para gestionar el despacho de vuelos, considerando la hora de salida programada y el estado de preparación del vuelo.
- Los vuelos que están listos para despegar tienen prioridad sobre los que aún no lo están.
- Antes de despachar se debe calcular la línea del horizonte. La línea del horizonte se calcula a partir de una lista de edificios y obstáculos en el área del aeropuerto. La entrada para calcular la línea del horizonte es un archivo de texto que contiene la posición y altura de los edificios y obstáculos. La salida es un archivo de texto que contiene la posición y altura de la línea del horizonte.
  
El sistema debe simular la operación completa de un aeropuerto. Los datos para la simulación los puede obtener de archivos de textos a definir 


## Requerimientos Adicionales:

El sistema debe simular la operación completa de un aeropuerto, utilizando datos de archivos de texto definidos por el grupo.
El sistema debe ser implementado en lenguaje de programación Go.
El proyecto debe ser desarrollado utilizando buenas prácticas de programación, incluyendo la correcta modularización del código y la documentación interna.
El informe técnico debe incluir:

- Diagramas y descripción de las estructuras de datos utilizadas.
- Descripción detallada de los algoritmos implementados.
- Análisis de la complejidad temporal y espacial de los algoritmos.
- Resultados de las pruebas con diferentes escenarios.
- Conclusiones sobre la eficiencia del sistema y posibles mejoras.

## Datos de Entrada

En la carpeta `data` se encuentran los archivos de texto que contienen ejemplos de los archivos de datos de entrada:

- `vuelos.txt`: Contiene la información de los vuelos programados, incluyendo número de vuelo, fecha y hora de salida programada, destino y aeronave asignada.
- `clientes.txt`: Nombre, Apellido, DNI y categoría de los clientes de una aerolínea, potenciales pasajeros.
- `aeropuertos.txt`: Contiene la información de los aeropuertos, incluyendo Provincia, Ciudad, Nombre del Aeropuerto y Código IATA (Código Internacional de 3 letras).
- `carga.txt`: Contiene la información de los paquetes de carga, incluyendo el destino, peso y volumen.
- `reservas.txt`: Contiene la información de las reservas de los pasajeros, incluyendo el número de reserva, Dni del pasajero, número de vuelo y estado de la reserva
- `edificios.txt`: Contiene la información de los edificios y obstáculos en el área del aeropuerto, incluyendo la posición inicial, altura y posición final de cada edificio u obstáculo.
- `aeronaves.txt`: Contiene la información de las aeronaves, incluyendo el código de la aeronave, el modelo, la capacidad máxima de carga y el número de asientos.