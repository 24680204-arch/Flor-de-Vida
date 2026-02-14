# Flor-de-Vida

Creación de una figura geométrica circular utilizando Python en Blender

-------

Este proyecto consiste en la creación automática de una figura geométrica compuesta por un círculo central y seis círculos distribuidos uniformemente a su alrededor.
Para su desarrollo se utilizó el lenguaje Python junto con la API de Blender llamada bpy, permitiendo generar objetos 3D mediante programación.

El patrón resultante forma una figura simétrica similar a una flor o estructura hexagonal, aplicando conceptos matemáticos como coordenadas polares y funciones trigonométricas.

------

Objetivo General

Desarrollar un script en Python que genere automáticamente una figura geométrica circular dentro de Blender.

-------
```Python
import bpy
import math
```
import bpy: Importa la librería principal de Blender. Permite acceder a los comandos de creación de objetos, edición y manipulación de la escena.

import math: Importa funciones matemáticas estándar. La necesitamos principalmente para usar cos, sin y radians

------
```Python
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()
```
2. Limpieza de la Escena
Antes de ejecutar el script, estas líneas seleccionan todos los objetos existentes y los eliminan. Esto asegura que cada vez que corras el código, empieces con un lienzo vacío y no se amontonen objetos anteriores.

-----
3. Configuración de Parámetros
```Python
radio = 3
angulo_actual = 0
paso_angular = 60  # 360 / 6
```
------
```Python
bpy.ops.mesh.primitive_circle_add(
    radius=radio,
    location=(0, 0, 0),
    vertices=64
)
```
Crea el primer círculo justo en el origen de coordenadas $(0, 0, 0)$.vertices=64 se usa para que el círculo se vea suave y no como un polígono de pocos lados.

-----
```Python
while angulo_actual < 360:

```
Inicia un ciclo que se repetirá hasta que el ángulo llegue a 360°.

------
```Python
rad = math.radians(angulo_actual)

```
Convierte el ángulo de grados a radianes.

-------
```Python
x = radio * math.cos(rad)
y = radio * math.sin(rad)
```
Convierte coordenadas polares a cartesianas:

x = r cos(θ)

y = r sin(θ)

-------
```Python
bpy.ops.mesh.primitive_circle_add(
    radius=radio,
    location=(x, y, 0),
    vertices=64
)
```
Crea un nuevo círculo en la posición calculada.

Cada vez que el ciclo se repite, se crea uno más alrededor

-------
```Python
angulo_actual += paso_angular
```
Aumenta el ángulo 60 grados para colocar el siguiente círculo en otra posición.

-------
Resultado final

Se obtiene:

1 círculo central

6 círculos alrededor

<img width="395" height="247" alt="image" src="https://github.com/user-attachments/assets/75f9dfcb-26c1-4ecb-8080-8bafcb89f063" />










-----


