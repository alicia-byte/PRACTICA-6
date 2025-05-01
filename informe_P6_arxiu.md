# Informe Práctica 6
## Ejercicio Practico 1 LECTURA/ESCRITURA DE MEMORIA SD
###  Descripción de la salida por el puerto serie
Cuando se ejecuta el programa, lo primero que aparece en el monitor serie es:
```cpp
Iniciando SD ...
```
Después pueden pasar tres cosas:
  -  Si todo está bien (la tarjeta está bien conectada y el archivo existe), se verá: 
  ```cpp
Inicialización exitosa
archivo.txt:
(contenido del archivo)
```

  -  Si la tarjeta SD no se puede iniciar (no está conectada o está mal), se verá: 
  ```cpp
No se pudo inicializar la tarjeta SD
```

  -  Si la tarjeta se inicia bien pero el archivo no existe o no se puede abrir, se verá: 
  ```cpp
Inicialización exitosa
Error al abrir el archivo
```

Si todo esta bien,se muestra el contenido del archivo `archivo.txt` en el monitor serie.


###  Explicación del funcionamiento
Este programa sirve para leer un archivo guardado en una tarjeta SD, usando el bus SPI del ESP32.

Lo que hace el código paso por paso es:

1. **Iniciar la comunicación por el puerto serie**
2. **Configurar los pines del SPI**
En este caso hemos definido los pines de la siguiente manera:
-   Pin 13 para el reloj (SCK)
    
-   Pin 12 para recibir datos (MISO)
    
-   Pin 11 para enviar datos (MOSI)
    
-   Pin 10 para seleccionar la tarjeta (CS)
3. **Iniciar la tarjeta SD**
4. **Abrir el archivo.txt**
5. **Cerrar el archivo**


## Ejercicio Practico 2 LECTURA DE ETIQUETA RFID

###  Descripción de la salida por el puerto serie
Cuando se conecta el módulo RFID y se abre el monitor serie, lo primero que se ve es:

 ```cpp
Lectura del UID
```

Esto significa que el lector RFID está listo para detectar tarjetas.

Cada vez que se acerca una tarjeta o llavero RFID, el lector lee su código único (UID) y lo muestra en el monitor serie:
 ```cpp
Card UID: 01 23 AB CD
```
Los números y letras varían dependiendo de la tarjeta, ya que cada una tiene su propio identificador.

###  Explicación del funcionamiento
Este código lo que permite es usar un lector RFID que se comunica con la ESP32 utilizando el bus SPI. Sirve para detectar cuando se acerca una tarjeta RFID y mostrar su código único en pantalla.

Lo que hace el código paso por paso es:

1. **Iniciar la comunicación por el puerto serie**
2. **Iniciar el bus SPI** 
- SPI.begin() 
3. **Iniciar el lector RFID** 
-  mfrc522.PCD_Init ()
4. **Esperar tarjetas**
5. **Leer la tarjeta**
6. **Finalizar lectura**
