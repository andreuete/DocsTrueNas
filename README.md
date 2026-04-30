# 🏠| Proyecto TrueNAS en casa
Documentación e instrucciones del proyecto de instalación de un sistema TrueNAS

`NOTA: parece hecho con chatgpt por los emojis, pero todo esto es 100% inteligencia artesanal. Lo juro 🙏😭`

# 👋| Introducción
En esta práctica vamos a implementar un servidor NAS para usarlo como un "Drive" en casa, aunque a este servidor se le pueden dar una infinad de usos.
Según la [web oficial](https://www.truenas.com/docs/scale/25.04/gettingstarted/scalehardwareguide/), los requisitos del sistema son los siguientes:

![Tabla de requisitos del sistema](/imgs/productos/requisitos.png)

Los 8gb de RAM aunque no sean estrictamente necesarios para el funcionamiento del propio sistema, si son altamente recomendados para que este tenga un rendimiento óptimo. Sobre todo a la hora de mover un gran volumen de archivos. 

# 💰| Presupuesto
| Img. | Producto | Precio | Cant. |
| -----| -------------- | ----- | ---|
| <img src="/imgs/productos/minipc.jpg" alt="Imagen del producto" width=auto height=80px> | [Mini PC LenovoThinkCentre M910q](https://www.amazon.es/Lenovo-Computer-ThinkCentre-Procesador-reacondicionado/dp/B0F99QY3GL/ref=sr_1_5?sr=8-5) | 150€ | 1x | 
| <img src="/imgs/productos/disco.webp" alt="Imagen del producto" width=auto height=80px> | [Disco duro HDD](https://www.pccomponentes.com/seagate-barracuda-35-2tb-sata-3) | 117€/Ud. | 2x |
| <img src="/imgs/productos/bahia.webp" alt="Imagen del producto" width=auto height=80px> | [Bahía SATA - USB](https://www.pccomponentes.com/tooq-tqds-805g-adaptador-hdd-ssd-2535-sata) | 25€ | 1x |

|Total: | ~400€ |
| ----- | ----- |
Una alternativa a la bahía puede ser conectar los distintos discos directamente al pc con adaptadores SATA - USB. He optado por la opción de la bahía porque esta cuesta solo un poco más que 2 adaptadores y es más fiable tener los discos ahi dentro que sueltos por ahí.
# 💾| Instalación
Descargamos la .iso de TrueNAS desde su [página oficial](https://www.truenas.com/download/) y creamos una unidad arrancable con [Rufus](https://rufus.ie/es/) (si estás Windows) o [Startup Disk Creator](https://computernewage.com/2018/08/18/crear-usb-booteable-gnu-linux/#utilidad-usb-arrancable) (si estás en Linux).

Una vez dentro del programa de instalación de TrueNAS, seleccionamos la opción **Install/Upgrade** y luego selecciona en que disco deseas instalar el S.O. Ese disco luego no podrá ser usado como pool de almacenamiento.

<img src="/imgs/instalacion/Instalacion4.png" alt="Imagen instalación" width=auto max-height=280px>
<img src="/imgs/instalacion/Instalacion7.png" alt="Imagen instalación" width=auto max-height=280px>

A continuación, nos pedirá que creemos una contraseña para el usuario *truenas_admin*, que será el que usaremos más adelante para acceder al panel web, y podemos elegir entre hacerlo desde el instalador o desde el panel web. 

<img src="/imgs/instalacion/Instalacion9.png" alt="Imagen instalación" width=auto max-height=280px>
<img src="/imgs/instalacion/Instalacion11.png" alt="Imagen instalación" width=auto max-height=280px>

Por último nos preguntará si queremos activar EFI boot. Selecciona que sí.

<img src="/imgs/instalacion/Instalacion12.png" alt="Imagen instalación" width=auto max-height=280px>

Cuando se haya terminado de instalar, el programa volverá a mostrar el mismo menú que al inicio. Esta vez selecciona **Reboot system** y desconecta la unidad arrancable.

<img src="/imgs/instalacion/Instalacion14.png" alt="Imagen instalación" width=auto max-height=280px>
<img src="/imgs/instalacion/Instalacion15.png" alt="Imagen instalación" width=auto max-height=280px>

# 🖥️| Panel
Al arrancar el servidor, veremos un menú con varias opciones y arriba de este la dirección a la que debemos conectarnos para acceder al panel. Si este diálogo no aparece, puedes cambiar la interfaz y configuración de red con las opciones 1 y 2 respectivamente.

<img src="/imgs/panel/Panel0.png" alt="Imagen instalación" width=auto max-height=280px>

Aquí iniciamos sesión con el usuario *truenas_admin* que configuramos antes.

<img src="/imgs/panel/Panel0.png" alt="Imagen instalación" width=auto max-height=280px>



