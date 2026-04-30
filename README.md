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
| <img src="/imgs/productos/disco.webp" alt="Imagen del producto" width=auto height=80px> | [Disco duro HDD 2TB](https://www.pccomponentes.com/seagate-barracuda-35-2tb-sata-3) | 117€/Ud. | 2x |
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

<img src="/imgs/panel/Panel0.png" alt="Imagen panel" width=auto max-height=280px>

Aquí iniciamos sesión con el usuario *truenas_admin* que configuramos antes.

<img src="/imgs/panel/Panel1.png" alt="Imagen panel" width=auto max-height=280px>

En la página principal podremos ver información general del servidor. El consumo del CPU y RAM, el uso de espacio en el disco, los componentes del servidor, etc.

<img src="/imgs/panel/Panel2.png" alt="Imagen panel" width=auto max-height=280px>

# Almacenamiento en Red
Para crear la unidad de almacenamiento en red nos dirigimos a la pestaña **Storage** y creamos una pool con los 2 discos duros.

<img src="/imgs/panel/Panel3.png" alt="Imagen panel" width=auto max-height=280px>
<img src="/imgs/panel/Panel4.png" alt="Imagen panel" width=auto max-height=280px>

Esta pool será en espejo, es decir, que ambos discos tendrán la misma información exacta para poder conservar los archivos en caso de avería.

<img src="/imgs/panel/Panel5.png" alt="Imagen panel" width=auto max-height=280px>
<img src="/imgs/panel/Panel6.png" alt="Imagen panel" width=auto max-height=280px>

Ahora, para poder acceder a esta unidad desde otro dispositivo hay que compartirla en red. Pero antes vamos a crear a un usuario. Esto se hace en **Credentials** > **Users**. Asegúrate de que el usuario tenga permisos para acceder al SMB

<img src="/imgs/panel/Panel10.png" alt="Imagen panel" width=auto max-height=280px>
<img src="/imgs/panel/Panel11.png" alt="Imagen panel" width=auto max-height=280px>

La unidad de almacenamiento "Fotos" no se puede compartir como tal, hace falta crear una directorio. Ve a la pestaña **Datasets** y crea uno.

<img src="/imgs/panel/permisos1.png" alt="Imagen panel" width=auto max-height=280px>
<img src="/imgs/panel/permisos2.png" alt="Imagen panel" width=auto max-height=280px>

Luego, selecciona el dataset, ve a **permissions** y **edit**. Aquí le damos al usuario permisos de modificar.

<img src="/imgs/panel/permisos3.png" alt="Imagen panel" width=auto max-height=280px>
<img src="/imgs/panel/permisos4.png" alt="Imagen panel" width=auto max-height=280px>

Finalmente, para acceder a la carpeta en red se hace introduciendo en la barra de búsqueda del explorador de archivos lo siguiente:
🪟| **Desde Windows**
`\\ip_del_servidor`
🐧| **Desde Linux**
`smb://ip_del_servidor`

<img src="/imgs/panel/carpeta1.png" alt="Imagen carpeta" width=auto max-height=130px>
<img src="/imgs/panel/carpeta2.1.png" alt="Imagen carpeta" width=auto max-height=130px>
<img src="/imgs/panel/carpeta3.png" alt="Imagen carpeta" width=auto max-height=130px>
