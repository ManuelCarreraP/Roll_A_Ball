# Mi Proyecto: Roll-a-Ball (Unity 2022.3)

Este es el primer juego que he creado siguiendo el tutorial de Unity. Es un juego sencillo donde manejas una bola, esquivas paredes y recoges cubos para ganar puntos.

## PASOS A REALIZAR

### 1. Preparar el escenario
Primero creé el suelo usando un "Plane" y le puse paredes a los lados con "Cubes" estirados. Lo más importante aquí fue resetear las posiciones a 0 para que nada saliera volando por error.

### 2. Crear el jugador (la bola)
Puse una esfera en el centro y, para que se moviera de verdad con gravedad y choques, le añadí un componente llamado **Rigidbody**. Sin esto, la bola se quedaría flotando y no respondería a las fuerzas.

### 3. Hacer que la bola se mueva
Escribí un script en C# (PlayerController). Básicamente, le dije al programa: "Si presiono las flechas del teclado o WASD, aplica una fuerza a la bola para que ruede". Usé una variable de velocidad (`speed`) que puedo cambiar desde fuera del código para que no vaya ni muy lento ni muy rápido.

### 4. La cámara que te sigue
Para que la cámara no se quedara quieta, le hice un script propio. No la puse dentro de la bola porque si no, la cámara giraría como loca cuando la bola rueda. El script calcula a qué distancia está la cámara de la bola y se encarga de mantener esa distancia siempre.

### 5. Los objetos para recoger (Pickups)
Creé unos cubos amarillos y les puse un script para que estén rotando todo el tiempo y queden bien. 
* Los puse como "Is Trigger". Esto hace que la bola pueda pasar por encima de ellos en lugar de chocar y salir rebotada. 
* Además, los convertí en **Prefabs**, así que si cambio el color de uno, todos los demás cambian automáticamente.

### 6. El sistema de puntos y el texto de ganar
Añadí texto en la pantalla usando el sistema de UI de Unity (TextMeshPro). 
* Cada vez que la bola toca un cubo, el cubo desaparece y el contador de puntos sube +1.
* Puse una condición: si recoges todos los cubos, aparece un mensaje grande que dice "WIN!".
