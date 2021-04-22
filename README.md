<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="./Doc/images/robot_no_bg.png" alt="Project logo"></a>
</p>

<h3 align="center">Noah Hardware</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)](/LICENSE)

</div>

---
Este repositorio contiene todas las instancias necesarias para el hardware del noah-robot; pero a diferencia el proyecto original en español y solo con componentes de mercadolibre y sin tarjetas propias o particulares. 

## Tabla de Contenidos

- [Tabla de Contenidos](#tabla-de-contenidos)
- [Contexto](#contexto)
- [Mecánica](#mecánica)
- [Electrónica](#electrónica)
- [Firmware](#firmware)
- [Videos](#videos)
- [Clonar el repo](#clone-the-repo)
- [Autores](#authors)

## Contexto

Como trabajo final de su tesis, [@GonzaCerv](https://github.com/GonzaCerv) decidio armar un robot de cero y compatible con turtlebot; pero tomando en cuenta que las piezas que lo componen puedan ser compradas en latinoamerica. Buscando un proyecto sobre el cual contruir una plataforma en comun para el desarrollo de ROS en los paises hipanoparlantes, La comunidad de ROS Es/Sp toma el proyecto con el objeto de replicarlo y potenciarlo.

Algunos de los repositorios hermanos originales se pueden encontrar en:

- [noah-hardware](https://github.com/GonzaCerv/noah-hardware).
- [noah-software](https://github.com/GonzaCerv/noah-software).
- [noah-docker](https://github.com/GonzaCerv/noah-docker).

## Mecánica

 <img width=400px src="Doc/images/Explode.png" alt="explode"></a>

El robot se encuentra estructuralemente compuesto por piezas impresas en 3D y algunas partes realizadas mediante corte laser de 3mm. Todas las partes fueron diseñadas en Solidworks. Usted puede encontrar estas tabti como otros archivos necesarios para la construccion de [la seccion de modelo 3D](./noah-hardware\Doc\3D_model).

Hay dos versiones del robot. La version **Noah** que utiliza la placa controladora principal propia y la genérica que es la que utilizara inicialmente la comunidad de ROS Es/Sp. 

- [Ensamble version genérica](Doc/assembly_generic.md).
  
<img width=500px src="images/../Doc/images/robot_generic.png" alt="Generic version"></a>
<img width=670px src="images/../Doc/images/noah_generic_2.jpg" alt="Generic version2"></a>

- [Ensamble version Noah](Doc/assembly_noah.md).
  
<img width=500px src="images/../Doc/images/robot_noah.png" alt="Noah version"></a>
<img width=390px src="images/../Doc/images/robot_noah2.png" alt="Noah version2"></a>

## Electrónica

<img src="Doc/images/PCB_finished.png" alt="pcb_finished"></a>

The main PCB is in charge of controlling all the peripherals of the robot. You can see in the pictures a all the connectors available. Several modules were provided:

- NEO6VM - GPS
- GY91 - IMU + Compass + Barometer + Temperature sensor
- ESP07 - Wifi module
- TB6612FGN - Dual full H bridge.

At the bottom there are 4 SMPS modules installed. They are capable of delivering up to 5A per channel.

The PCB was designed with Kicad. Take a look to the [PCB section](./noah-hardware\Doc\PCB).

## Firmware

The STM32F407VG was choseen as the main controller of this board. It runs at 72Mhz, enough to manage the 4 main FreeRTOS tasks that are currently coded:

- PID control loop for left motor.
- PID control loop for right motor.
- Comms task: provides communication between this layer and the ROS layer.
- Power management: small task in charge of managing the energy of the power supplies.

This project uses [STM32CubeIde](https://www.st.com/en/development-tools/stm32cubeide.html).

## Videos

- [Exploded view of the robot](https://youtu.be/NDaXydzkYNs)
- [Working demo of the robot](https://youtu.be/hgb2TbaiBBA)

## Clone the repo

- Install LFS in your machine:
  
  ```bash
  git lfs install
  ```

- clone the repo:
  
  ```bash
  git clone git@github.com:GonzaCerv/noah-hardware.git
  ```

## Authors

- [Gonzalo Cervetti](https://github.com/GonzaCerv) - Idea & Initial work
