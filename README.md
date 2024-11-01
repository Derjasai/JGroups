# Laboratorio JGroups

App para aplicaciones distribuidas las cuales son capaces de compartir un mismo state, en este caso una lista donde se almacena el historial de mensajes de un mismo group

## Tecnologias

- Apache Maven: 3.9.1
- GIT
- Java: 17
- JGroups 5.0.0

## Arquitectura
La arquitectura utilizada para ese proyecto se realiza en un VM, en este caso seleccionamos un servicio EC2 de AWS, en esta VM generamos 3 users con el proyecto ya instalado y corriendo donde pueden hacer uso del aplicativo en común.

![image](https://github.com/user-attachments/assets/ffce6f2c-602d-4133-a221-c1a4d75a0933)

Como se puede apreciar en la imagen el proyecto esta realizado en Java, usando JVM (Java Virtual Machine) para poder correrlo, así mismo el aspecto mas importante dle proyecto es el uso de la librería JGroups, la cual es la que nos permite la comunicación entre los usuarios conectados al mismo grupo.

## Correr el proyecto

Previamente a la instalacion del repositorio asegurarse de tener tanto GIT, MVN como Java instalados con las versiones que se indicaron previamente

Descargar o clonar el proyecto y entrar a la carpeta Root.
`git clone https://github.com/Derjasai/JGroups.git`

### Inicializar el Backend
Dentro de la carpeta root del proyecto correr el siguiente comando

`mvn clean install`

Despues de que termine de compilar, ejecutar el siguiente comando en la misma carpeta root

`mvn exec:java -D exec.mainClass="org.example.SimpleChat"`

## Proceso de SetUp
1. Una vez creamos nuestra VM EC2 en AWS procedemos conectarnos a ella mediante SSH.°
2. Cuando hayamos ingresado a la máquina con el user por defecto `ec2-user` creamos dos user adicionales `new-user-1` y `new-user-2`
3. Para el correcto despliegue de nuestro proyecto necesitaremos hacer uso de MVN, Java y GIT, por lo que corremos los siguientes comandos en la VM para poder obtener estos programas `sudo yum install maven` y `sudo yum install git` (Al instalar maven instalamos una version de Java, por lo que no necesitamos hacerlo por separado).
4. Una vez tengamos todo instalado descargamos el repo con `git clone https://github.com/Derjasai/JGroups.git`
5. Entramos a la carpeta root del proyecto `cd JGroups`
6. Y ejecutamos mvn para instalar dependencias `mvn clean install`
7. Una vez las dependencias hayan sido instaladas y compilados corremos nuestro proyecto usando `mvn exec:java -D exec.mainClass="org.example.SimpleChat"` en windows o `mvn exec:java -Dexec.mainClass="org.example.SimpleChat"` en Linux
8. Logeate con otro user sin cerrar la conexión SSH del user donde estas actualmente.
9. Replicas desde el paso 4 hasta haberlo hecho con la cantidad de users que hayas creado.

## Video Demo Del Despliegue

Como prueba del despliegue realizado se grabó el siguiente video para demostrar el funcionamiento, así mismo sirve como tutorual paso a paso para poder desplegar el proyecto en una EC2.

[video-demo](https://youtu.be/vh1lRIMKFOw)!

# Version
1.0

# Author
Daniel Esteban Ramos Jimenez
