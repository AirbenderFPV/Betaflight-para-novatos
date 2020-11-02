# Betaflight-para-novatos

# Betaflight para novatos

<img src="https://raw.githubusercontent.com/wiki/betaflight/betaflight/images/betaflight/bf_logo.png">

¿Eres nuevo en el mundo del FPV y no sabes lo que Betaflight puede hacer por ti?

En este repositorio enseñare las cosas basicas que un novato tiene que saber de **Betaflight 4.2.x** así como las configuraciones recomendadas.  
Recordad que para usar esta versión de Betaflight es necesario el **Betaflight Configurator version 10.7.0**.  
El uso de esta información queda bajo la responsabilidad de cada usuario.  

Si tienes dudas de como descargarte el configurador o como alcualizar el firmware visita los repositorios:  

[Actualizar firmware 4.2.x]   
https://github.com/AirbenderFPV/Actualizar-Firmware

[Actualizar/Instalar el Configurador de Betaflight v10.7]  
https://github.com/betaflight/betaflight-configurator/releases/download/10.7.0/betaflight-configurator-installer_10.7.0_win32.exe

## Menú Betaflight 4.2.x  

### Pantalla de Puertos

En esta pantalla podremos configurar los puertos de nuestro quad.  
Estos puertos normalmente vienen definidos en la placa controladora con la etiqueta TX y acompañada de un numero.  
Por ejemplo, el TX3 en la placa controladora sera el puerto Uart3 en Betaflight.  

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/puertos.PNG">

En esta imagen tenemos habilitado:   
El puerto **USB VCP** para la comunicación por el puerto usb.  
El puerto **UART1** para  la comunicación Rx. Comunicación con nuestra emisora.  
El puerto **UART3** para la comunicación con el VTX a través de SmartAudio.  
El puerto **UART4** para la comunicación por Bluetooth. Con aplicación SpeedyBee.
En algunos casos el **UART6** se utiliza para la telemetria con los ESC, tendriamos que declararlo en **Entrada de Sensores**

No todas las controladoras tienen Bluethooth y no todos los VTX tienen cable para comunicarción.
Puedes consutar los puertos y configuraciones recomendadas por el fabricante en el manual de tu controladora de vuelo, como en los siguientes ejemplos:  

[MAMBA F405MK2] https://www.diatone.us/collections/mamba-stack/products/mamba-f405-mk%E2%85%B1-flight-controller-stack

[MAMBA F722] https://www.diatone.us/collections/mamba-stack/products/mamba-f722s-flight-controller-stack

### Pantalla de Ajustes  

En esta pantalla podremos calibrar, restaurar o hacer una copia de seguridad nuestro quad.

En esta versión de Betaflight es **obligatorio calibrar** nuestro quad si vamos a usar los modos **Angle** o **Horizon**.

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/Ajuste.PNG">

Para **Calibrar el Acelerómetro** situar nuestro quad en una superficie plana y dar al botón.  
Si usamos **Borrar Contiguración** volveremos a los valores de fabrica la controladora de vuelo.  
Si queremos hacer una **Copia de seguridad** de nuestra configuración, usando ese botón nos abrirá el explorador de windows para que indiquemos donde guardar el archivo.  
Para **Restaurar** una copia de seguridad solo tendremos que indicar el archivo donde previamente lo guardamos.  
 
Es aconsejable hacer una copia de seguridad antes de hacer cambios importantes, por si tenemos que deshacer estos cambios de forma rapida.

### Pantalla de Configuración  

En esta pantalla podremos configurar el protocolo que controlara nuestros motores y las diferentes funcionalidades de nuestro quad.  
Es una de las pestañas mas importante de la configuración de nuestro quad. 
Puedes dar nombre a tu quad en el subapartado **Personalización**  

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/configuracion.PNG">

_Ejemplo: Configuración usada en una controladora MAMBA STM32F722S_

#### Funcionalidades ESC/Motor:
La opción **MOTOR_STOP** controla si los motores girarán o no al armar el quad.  
Si los motores giran al armar el quad y tenemos esta opción deshabilitada seguramente tendremos habilitado el **AIR MODE**.  
Por defecto el **Motor Idle Throttle value [percent]** tiene un valor de 4.5, esto es el porcentaje al que giraran los motores al armar.  
Por defecto el numero de **Polos del motor** viene como 14. Estos son el numero de imanes que tiene tu campana de motor.  
En tinnys a veces este numero se reduce ya que los motores son mas pequeños. Rondan sobre 12.  
Lo mejor es asegurarse mirando una campana de nuestros motores.  

#### Configuración del sistema y DShot settings:  

El **Acelerómetro** es el sensor que nos ayuda a controlar la inclinazión del quad.    
En caso de volar en **Angle Mode** o **Horizon Mode** necesitas tener activado este sensor.  
Revisa la pantalla de Ajustes para ver como calibrar el quad si usas esos modos.  
Normalmente las controladoras de vuelo no trae equipado un Barómetro ni un Magnetómetro.   
Lo mejor en estos casos es **Desactivar** estos dos sensores.  

Las frequencias del sersor Giro y del PID son importantisimas para volar.  
Estas estan condicionadas a el tipo de controladora de vuelo tengamos, una F7 irá mejor que una F4.  
Si tienes poca experiencia es mejor dejar los ajustes por defecto.  
Consulta en las especificaciones de tus ESCs o 4in1 que DSHOT tiene antes de aplicar cualquier corrección.  
Se puede habilitar el bidirectional con el switch **DShot Bidirectional**.  
También hay que consultar en las especificaciones de tus ESCs o 4in1 si lo soporta.  

- Con el filtro rpm habilitado   
dshot300 -> 4k max pidloop (Recomendable para controladoras F4)  
dshot600 -> 8k max pidloop (Recomendable para controladoras F7)   

- Usando el bidirectional y con el filtro rpm habilitados:     

dshot150 -> 2k max pidloop   
dshot300 -> 4k max pidloop (Recomendable para controladoras F4)     
dshot600 -> 8k max pidloop (Recomendable para controladoras F7)    

- Sin usar el bidirectional y con el filtro rpm habilitados:    

dshot150 -> 4k max pidloop (Recomendable para controladoras F4)   
dshot300 -> 8k max pidlopp (Recomendable para controladoras F7)  
dshot600 -> up to 16k max pidloop (8k es el maximo que se puede configurar en la versión 4.2)  

Para la actualización de firmware de los ESC o 4in1 visita:

[Repertorio ESC and 4in1] https://github.com/AirbenderFPV

#### Armado y Aliniación de Placa y Sensores:

Si tenemos el Acelerómetro activado, habilitaremos la selección del Ángulo de armado máximo.  
Personalmente recomiendo el valor **180º** para poder armar el quad bajo cualquier inclinación.  

En cuanto a la aliniación de la placa, si la montamos de forma que la flecha dibujada en la controladora de vuelo apunte hacia delante, todos los valores tienen que ser cero.


<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/configuracion2.PNG">

#### Receptor: 

En este subapartado podemos configurar como será la comunicación con nuestra emisora.  
Debes consultar el protocolo de tu receptor y tu emisora para configurarlo.

#### Otras funcionalidades:

Normalmente se dejan tal como vienen de serie a excepción de estas tres:

- Air Mode:  
Activa permanentemente el Air Mode. Se puede deshabilitar aqui i condicionarlo en la pantalla de Modos.  
- OSD:  
Permite sobreponer información sobre la imagen de la camara. Se configura en la pantalla de OSD.  
- LED_STRIP:  
Nos ayuda a controlar los leds del quad. Se pueden configurar en su pantalla.  
- ESC TELEMETRY:  
Habilita telemetria con los ESC. Consultar la pantalla de puertos. 


### Pantalla de Energía y Batería

Esta pantalla nos ayuda con la gestión de el voltage y la corriente de nuestro quad. 

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/energia.PNG">

**Valores por defecto, no editar**  
El voltaje mínimo de celda nunca debe bajar de 3.3v.  
Si bajamos el voltaje de una celda por debajo de 3.3v podemos dañar la Lipo.   
El voltaje de aviso por defecto se configura en 3.5v.  
Este voltaje es el que determina en el OSD cuando aparece el aviso de _LOW VOLTAGE_    
Si eres novato y no estas muy pendiente de la bateria mejor subir el voltaje de aviso a 3.6v.  

Para calibrar el sensor de voltaje tendremos que usar un Multimetro para saber el voltaje real de nuestra bateria.   
Posteriormente enchufar la LiPo y incrementar/disminuir el valor de **Escala** en el medidor de voltaje hasta que el valor del medidor de voltaje concuerde con el medido con el multimetro. 

Para calibrar el sensor de corriente podemos usar el **ADC Integrado** y ajustar el escalado tal como marca el fabricante o podemos usar la opción **Sensor ESC** si previamente lo hemos configurado en los puertos.

Puedes consutar los escalados recomendados por el fabricante en el manual de tu controladora de vuelo, como en los siguientes ejemplos:  

[MAMBA F405MK2] https://www.diatone.us/collections/mamba-stack/products/mamba-f405-mk%E2%85%B1-flight-controller-stack

[MAMBA F722] https://www.diatone.us/collections/mamba-stack/products/mamba-f722s-flight-controller-stack

Para mas información visita:  

[Repertorio Baterias] https://github.com/AirbenderFPV/Baterias

### Pantalla de Modo de Seguridad

(Tenemos que habilitar el modo experto en la parte superior derecha de Betaflight Configurator)

Lo mejor es dejarlo por defecto para que nuestro quad en caso de perdida de señal se desarme.

### Pantalla de Ajustar PID

#### PID  
Esta pestaña nos ayuda a calibrar el PID de nuestro quad, si tienes poca experiencia es mejor dejar los ajustes por defecto.

[PID] https://github.com/AirbenderFPV/PID-Betaflight-4.2

#### TASAS  
Esta pestaña nos ayuda a calibrar los "rates" o tasas de nuestro quad, en otras palabras la sensibilidad de nuestros sticks.   
Podemos editar el perfil de cada palanca editando los valores para respuestas mas ajustadas a nuestra forma de volar.  
Si tienes poca experiencia es mejor dejar los ajustes por defecto.  

#### FILTROS  
Esta pestaña nos ayuda a filtrar las señales de nuestro quad, si tienes poca experiencia es mejor dejar los ajustes por defecto.  

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/Filtros.PNG">

Es muy recomendable en esta pestaña editar los valores del **Filtro Notch Dinámico** situado en la parte inferior izquierda.  
Los valores recomdendados y provados por Joshua Bradwell son los que aparecen en la imagen.  
Giro Filtro Notch Dinámico Ancho = 0  
Giro Filtro Notch Dinámico Q =250   
Giro Filtro Notch Dinámico Min =90   
Giro Filtro Notch Dinámico Max =350   

Además, los valores multiplicadores **Filtro Giro** y **Filtro D Term** se pueden mover un poco para filtrar menos la señal que enviamos a nuestro quad y tener una respuesta mas rapida. Hay que mover los dos por igual.  

Personalmente he provado el valor **1.2 en ambos**, si provais alguno y no os convence volver a el valor por defecto 1 en ambos.  

Para mas información de ajustes rapidos recomendados visita:

[Ajustes rapidos recomendados en Betaflight 4.2.x] https://github.com/AirbenderFPV/Ajustes-rapidos-recomendados-en-Betaflight-4.2.x



### Pantalla de Receptor

Esta pantalla nos ayuda a ver las señales de nuestra emisora.
Si tenemos la emisora encendida y el quad conectado al ordenador y no varian los valores, seguramente tengamos que alimentar el quad con una LiPo.  
Recordad tener siempre la antena del VTX conectada antes de enchufar una LiPo y no estar mucho rato con el quad parado y la LiPo alimentando.**Podríais sobrecalentar el sitema e incluso quemar el VTX.**

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/receptor.PNG">

En esta pantalla es importante que seleccionemos el **Canal RSSI** para saber el estado de nuestra señal durante el vuelo.

### Pantalla de Modos

Esta pantalla nos ayuda a configurar los **MODOS** de nuestro quad.


### Pantalla de Correcciones

(Tenemos que habilitar el modo experto en la parte superior derecha de Betaflight Configurator)

### Pantalla de Servos

(Tenemos que habilitar el modo experto en la parte superior derecha de Betaflight Configurator)

### Pantalla de Motores

### Pantalla de OSD

### Pantalla de Transmisor de Video

Esta pantalla nos ayuda a configurar el VTX.  
Para ello sera necesario tener la tabla de nuestro VTX (Archivo.JSON) y tener configurado el Uart pertinente.  

[Repertorio VTX] https://github.com/AirbenderFPV/VTX

### Pantalla de Sensores

(Tenemos que habilitar el modo experto en la parte superior derecha de Betaflight Configurator)

### Pantalla de Registro Conectado

(Tenemos que habilitar el modo experto en la parte superior derecha de Betaflight Configurator)

### Pantalla de Caja Negra

La caja negra nos ayuda a guardar datos de los sensores en tiempo real para su posterior analisis.  
Para un mejor rendimiento de la controladora de vuelo, si no vamos a usar la caja negra, es mejor desactivarla.

[Notas de la versión] https://github.com/betaflight/blackbox-log-viewer/releases

Descarga el software para ver los log de la caja negra:  
https://github.com/betaflight/blackbox-log-viewer


### Pantalla de CLI

Esta pantalla nos permite introducir comandos para programar o extraer valores de la controladora de vuelo de nuestro drone  
Para guardarlos tenemos que ejecutar el comando **Save**.

Podemos listar nuestros ajustes cambiados respecto a los valores por defecto con el comando **diff_all**


#### Fuentes de información

[Notas oficiales de la versión] https://github.com/betaflight/betaflight/wiki/4.2-Tuning-Notes  

[Joshua Bardwell] https://www.youtube.com/watch?v=rhfOVJMxY7E  

[QuadMx Drones] https://www.youtube.com/watch?v=tCgN-EwdSQ8   
 
[Midronedecarreras] https://www.midronedecarreras.com/betaflight/#Descarga_el_Configurador_BLHeli_suite_32  

[Airbender_FPV] https://www.instagram.com/airbender_fpv/
