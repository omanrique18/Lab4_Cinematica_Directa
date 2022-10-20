# Lab4_Cinematica_Directa
## Caracterización del robot
Se realizó la caracterización de un robot PincherX 100. Primero se tomaron medidas de la longitud de cada eslabón que conforma el manipulador y se registraron en el siguiente gráfico:
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196854680-279757b2-7256-4268-9ed0-d8be35b78b06.png" width="350" />
</p>

Una vez tomadas las medidas se escogen los marcos de referencia y se crea la tabla de parámetros DH:
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196854772-def9fbae-411c-430d-bae5-25dde2257b5f.png" width="350" />
</p>

## ROS
Primero creamos la carpeta catwin_ws, con una carpeta src dentro, la cual va a contener todos los recursos para la correcta ejecución del script de python que moverá el pincher. Para esto ejecutamos el siguiente comando:
```bash
cd ~/catwin_ws/src
```
Posteriormente clonamos el repositorio con los archivos antes mencionados en la carpeta src:
```bash
git clone https://github.com/felipeg17/px_robot
```
Ejecutamos el siguiente comando
```bash
cd ..
source devel/setup.bash
```
Verificamos el puerto al que está conectado el robot (usualmente es el USB0)
```bash
ls /dev/tty*
```
Damos los permisos respectivos al puerto USB0
```bash
sudo chmod 777 /dev/ttyUSB0
```
Ejecutamos las siguientes lineas de código 
```bash
catkin build px_motor
source devel/setup.bash
```
Ejecutamos el launch
```bash
roslaunch px_robot px_controllers.launch
```
###Script de python
Se creó un script que en primer lugar mueve articulación por articulación el robot hasta producir la siguiente rutina de poses:
1. [0 0 0 0 0]
2. [20° 0 0 0 0]
3. [20° 20° 0 0 0]
4. [20° 20° 20° 0 0]
5. [20° 20° 20° 20° 0]

Después de una pausa, el robot genera una nueva rutina de 5 poses distintas:
1. [0 0 0 0 0]
2. [-20 20 -20 20 0]
3. [30 -30 30 -30 0]
4. [-90 15 -55 17 0]
5. [-90 45 -55 45 10]

Este script debe estar guardado en /catwin_ws/src/px_robot/scripts. Para ejecutarlo, se abre la carpeta scripts desde Visual Studio Code, se abre el script y se presiona el botón "Run".

## Matlab
Se grafican cada una de las poses solicitadas a continuación:
1. [0 0 0 0 0]
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196855005-d51bf285-0bb6-4f5a-8b44-13c222548d99.jpeg" width="350" />
</p>
2. [20° 20° 20° 20° 0]
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196855129-652046ea-e7bb-4d7b-b498-cd2e8e1e4454.jpeg" width="350" />
</p>
3. [-20 20 -20 20 0]
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196855214-1fd7ca6f-8060-4c1d-b6c5-dce73b25c216.jpeg" width="350" />
</p>
4. [30 -30 30 -30 0]
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196855254-e0dfaae9-4dab-47de-a65e-7e9b8e3ec3c1.jpeg" width="350" />
</p> 
5. [-90 15 -55 17 0]
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196855304-28b6b72d-def6-476c-ba06-d87e787c6ef3.jpeg" width="350" />
</p>
6. [-90 45 -55 45 10]
<p align="center">
  <img src="https://user-images.githubusercontent.com/51519737/196855373-0d5df0fa-8802-4385-a50d-e070422c92ba.jpeg" width="350" />
</p>

## Practica
A continuación se muestra el video con las rutinas de poses del robot.

[![Alt text](https://img.youtube.com/vi/I8mTUED6GBQ/0.jpg)](https://youtu.be/I8mTUED6GBQ)

## Integrantes
- Juan Andres Bueno Hortua
- Oscar Javier Manrique Merchan

## Profesores
- Ricardo Emiro Ramirez Heredia
- Jhoan Sebastian Rodriguez Rodriguez
