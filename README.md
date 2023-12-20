# Instalar Apps en Changan CS35 plus

Este proyecto tiene como objetivo ofrecer una solución no oficial para la instalación de aplicaciones en la pantalla de fábrica del automóvil Changan CS35 Plus. Ten en cuenta que este proceso implica modificar la configuración del sistema de fábrica y se debe realizar bajo tu propio riesgo.

## Advertencia

**¡IMPORTANTE! Este proyecto es un esfuerzo no oficial y no está respaldado ni garantizado por el fabricante del vehículo. La modificación del sistema puede tener consecuencias no deseadas, incluida la pérdida de garantía, el riesgo de malfuncionamiento y daño permanente al dispositivo. Úsalo con precaución y asume plena responsabilidad por cualquier resultado.**


## Índice

1. [Requisitos](#requisitos)
2. [Preparar APK](#prepararapk)
3. [Uso](#uso)
4. [Contribución](#contribución)
5. [Licencia](#licencia)

## Requisitos

Antes de comenzar con la instalación, asegúrate de cumplir con los siguientes requisitos:

- **Changan CS35 Plus:** Este proceso está diseñado específicamente para el modelo CS35 Plus.
  
- **Usb:** Un dispositivo usb con musica sera de ayuda para acelerar el proceso de conexion. 
  
- **Cable usb A a A o C to A :** Será necesario un cable USB para conectar tu dispositivo al sistema del vehículo, se recomienda usar el tipo A para conectar al carro y que el cable sea de buena calidad. Esto es crucial, ya que algunos cables de baja calidad pueden no ser compatibles con ciertos procesos, como ADB (Android Debug Bridge).

- **Laptop Windows:** Será necesario una laptop con sistema operativo windows con puertos usb c o a dependiendo del tipo de cable a usar.

- **ADB:** Puedes descargar ADB aca:https://developer.android.com/studio/releases/platform-tools?hl=es-419 .

- **Conocimientos Básicos:** Es recomendable tener conocimientos básicos sobre codigo bash.

## Preparar APK
1. Obtener el apk a usar.
2. Crear una carpeta preferiblemente en la misma carpeta del adb a usar.
3. Utilizar 7zip, winrar o similar para abrir el apk.
4. Copiar el contenido de la carpeta lib.
5. Pegar el contenido de la carpeta lib en nuestra carpeta.
6. En la carpeta lib ubicar si se encuentra las carpetas arm**v7, copiarlas y cambiarles el nombre a arm.
7. Borrar las demas carpetas.

**Tener en cuenta que las aplicaciones que requieran servicios externos no van a funcionar y corren el riesgo de congelar la radio**
**Se tiene un espacio limitado de memoria y almacenamiento en la radio si esta se llegase a llenar hara que la radio no vuelva a iniciar**
**Se recomienda solo usar 1 app a la vez**

## Uso

1. Con la radio encendida, inserta el usb con la musica y espera a que este empiece a reproducir.
2. Una vez este reproduciendo la musica, ingresa a la opcion de marcado telefonico de la radio e ingresa el siguiente nuemero #*#*888 y presiona llamar.
3. Debera aparecer un teclado numerico, ingresa el siguiente codigo 963215.
4. Debera aparecer el menu avanzado, en la segunda opcion selecciona la opcion de ADB.
5. La musica deberia cortarse hasta este punto, retira el dispositivo usb e inserta el cable usb.
6. conecta el cable a la laptop e ingresa a la carpeta ADB.
7. Ingresa el siguiente comando
   ```bash
   abd devices
8. Debera aparecer un dispositivo conectado
9. Ingresa el siguiente comando:
    ```bash
    adb root
10. Ingresa el siguiente comando:
    ```bash
    adb remount
11. Validaremos el espacio disponible en la radio (Importante)
    ```bash
    adb shell df -h
11. Utilizaremos el almacenamiento de usuario para guardar nuestras apps. Para ello usaremos el siguiente comando:
    ```bash
    adb push 'nombredelacarpeta'/ /user_data/
12. Ingresemos al shell
    ```bash
    adb shell
13. Ingresamos a la carpeta que hemos cargado a la radio:
    ```bash
    cd /user_data/'nombredelacarpeta'
14. Le damos permisos al apk.
    ```bash
    chmod 644 'nombredelapk.apk'
15. Debemos crear un link en el sistema de la radio para que aparezca en el menu.
    ```bash
    cd /system/app/
    ln -s /user_data/'nombredelacarpeta'/'nombredelapk.apk' /system/app/
16. Debemos dar permiso al link creado para que aparezca en el menu principal
    ```bash
    chmod 644 nombredelapk.apk
17. Reiniciamos el dispositivo mediante adb.
    ```bash
    exit
    adb reboot
18. Si todo salio bien la radio se reiniciara y en el menu aparecera la applicacion.
    
