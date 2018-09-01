# Xiaomi Mi Plant y Node-RED


## Descripción del proyecto


Xiaomi Mi Plant es un dispositivo con el que podremos controlar la humedad, la fertilidad, la temperatura y la luz ambiental de la planta en la que lo situemos. Usa Bluetooth de baja energía para la comunicación con el exterior y tiene su propia aplicación para teléfono móvil. 

Node-RED es una herramienta de visualización open-source creada por IBM (IBM Emerging Technology) y que nos permite interconectar todos nuestros elementos al Internet de las cosas.

Este proyecto une ambos sistemas, permitiéndonos ver gráficamente los datos que el sensor de planta nos envía y en un futuro poder enviarlos a una nube para su análisis.

## Funcionamiento

Después de situar el sensor en una planta el software de Node-RED, utilizado en una Raspberry Pi, se encarga de estos procesos cíclicamente:

  1. Buscar, por su dirección Bluetooth "xx:xx:xx:xx:xx:xx", durante un tiempo programable si el dispositivo está dentro de su alcance.
  2. Si lo encuentra, lee sus servicios, características y se conecta a él.
  3. Una vez conectado, es necesario escribir un dato {0xA0, 0x1F} en la siguiente característica "00001a00-0000-1000-8000-00805f9b34fb" para que nos transmita la información.
  4. Ahora recibe la información en la característica "00001a01-0000-1000-8000-00805f9b34fb" y se formatea para separar cada uno de los datos del sensor.
  5. Finalmente la temperatura, humedad, luminosidad y la fertilidad se muestran de forma gráfica.

El proyecto se puede ampliar leyendo también el firmware del sensor y el nivel de batería. 

### Esquema de nodos del proyecto


![Nodos proyecto](https://raw.githubusercontent.com/moisesfa/Proyectos_Node_Red/master/XiaomiPlant/img_XiaomiPlant/cap_Xmiplant_10.png)

### Dashboard del proyecto 

![Dashboard proyecto](https://raw.githubusercontent.com/moisesfa/Proyectos_Node_Red/master/XiaomiPlant/img_XiaomiPlant/cap_Xmiplant_08.png)

## Referencias a Módulos Node-RED

Para el tratamiento del Bluetooth BLE se utiliza el módulo:
[node-red-contrib-ignoble](https://www.npmjs.com/package/node-red-contrib-ignoble)

Para mostrar los datos gráficamente se utiliza el módulo:
[node-red-dashboard](https://www.npmjs.com/package/node-red-dashboard)

## Licencia

Copyright (c) <2018> Moisés Fernández Arias

Se concede permiso, libre de cargos, a cualquier persona que obtenga una copia de este software y de los archivos de documentación asociados (el "Software"), para utilizar el Software sin restricción, incluyendo sin limitación los derechos a usar, copiar, modificar, fusionar, publicar, distribuir, sublicenciar, y/o vender copias del Software, y a permitir a las personas a las que se les proporcione el Software a hacer lo mismo, sujeto a las siguientes condiciones:

El aviso de copyright anterior y este aviso de permiso se incluirán en todas las copias o partes sustanciales del Software.

EL SOFTWARE SE PROPORCIONA "TAL CUAL", SIN GARANTÍA DE NINGÚN TIPO, EXPRESA O IMPLÍCITA, INCLUYENDO PERO NO LIMITADA A GARANTÍAS DE COMERCIALIZACIÓN, IDONEIDAD PARA UN PROPÓSITO PARTICULAR Y NO INFRACCIÓN. EN NINGÚN CASO LOS AUTORES O PROPIETARIOS DE LOS DERECHOS DE AUTOR SERÁN RESPONSABLES DE NINGUNA RECLAMACIÓN, DAÑOS U OTRAS RESPONSABILIDADES, YA SEA EN UNA ACCIÓN DE CONTRATO, AGRAVIO O CUALQUIER OTRO MOTIVO, DERIVADAS DE, FUERA DE O EN CONEXIÓN CON EL SOFTWARE O SU USO U OTRO TIPO DE ACCIONES EN EL SOFTWARE. 