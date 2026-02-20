# Roll A Ball - Unity 2022.3

Este proyecto es el resultado de seguir el tutorial oficial de Unity para principiantes. En él se aplican los conceptos fundamentales de la creación de videojuegos 3D, el uso de físicas y la programación en C#.

## Descripción del Proyecto
El juego consiste en controlar una esfera (jugador) a través de un escenario para recolectar objetos. Se centra en el aprendizaje de las herramientas del editor de Unity, la gestión de componentes y la lógica de colisiones.

## Pasos Realizados en el Tutorial

### 1. Configuración de la Escena
Se preparó el entorno de juego utilizando objetos 3D básicos:
* **Ground (Suelo):** Un plano posicionado en el origen (0,0,0) que sirve como base.
* **Walls (Paredes):** Cubos escalados para rodear el suelo, evitando que el jugador se caiga del escenario.
* **Materiales:** Se crearon y aplicaron materiales para diferenciar visualmente el suelo, las paredes y los objetos.

### 2. El Jugador y su Movimiento
Se creó el objeto "Player" (una esfera) y se configuró para interactuar con el mundo físico:
* **Rigidbody:** Se añadió este componente para que el motor de física controle la gravedad y las colisiones de la esfera.
* **Script de Control:** Se programó el script `PlayerController.cs`. Este detecta la entrada del teclado (ejes Horizontal y Vertical) y aplica una fuerza constante al Rigidbody mediante el método `FixedUpdate()`, que es el estándar para cálculos físicos.

### 3. Sistema de Seguimiento de Cámara
En lugar de emparentar la cámara directamente al jugador, se creó un script llamado `CameraController.cs`.
* **Lógica del Offset:** El script calcula la distancia inicial entre la cámara y la esfera. En cada frame (usando `LateUpdate`), la cámara se reposiciona manteniendo esa distancia exacta, lo que evita que la cámara gire cuando la bola rueda.

### 4. Creación de Coleccionables (Pickups)
Se diseñaron los objetos que el jugador debe recoger:
* **Prefabs:** Se creó un cubo inclinado y se convirtió en un "Prefab". Esto permitió distribuir múltiples copias por el escenario de forma que cualquier cambio en el original se aplique a todos automáticamente.
* **Script de Rotación:** Un pequeño script hace que los cubos giren sobre sus ejes para que sean visualmente atractivos.
* **Triggers:** Se activó la opción "Is Trigger" en el Collider de los coleccionables para que la bola pueda "atravesarlos" y detectarlos sin chocar físicamente.

### 5. Gestión de Colisiones y Puntuación
Se implementó la lógica necesaria para que el juego reconozca el progreso:
* **Etiquetas (Tags):** Se asignó el tag "PickUp" a los coleccionables para que el script del jugador pueda identificarlos al tocarlos.
* **OnTriggerEnter:** Dentro del script del jugador, se programó que al entrar en contacto con un objeto "PickUp", este se desactive de la escena.
* **Interfaz de Usuario (UI):** Se utilizó el sistema de TextMeshPro para crear un marcador que muestra el número de objetos recogidos y un mensaje final al completar el nivel.
