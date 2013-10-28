TEMA 1 IV: Ejercicios clase Antonio Melero Bello
================================================

### Ejercicio 1

https://github.com/franciscomanuel/Clase-30-de-septiembre

### Ejercicio 2

### Ejercicio 3

¿Qué tipo de virtualización es la más adecuada para: alojar varios clientes en un sólo servidor, crear un sistema 
efiiciente de web + middleware + base de datos, un sistema de prueba de software e integración continua? Responder 
y razonar.

> Alojar varios clientes en un sólo servidor: El tipo de virtualización para este caso sería la virtualización plena 
ya que al haber múltiples usuarios necesitamos proporcionarles a cada uno de ellos una máquina virtual completa de forma 
independiente.
Crear un sistema eficiente de web + middleware + base de datos: En este caso la virtualización de aplicaciones ya que 
empaqueta aplicaciones de forma que se ejecuten en un entorno que las aísla del resto del sistema operativo, es decir, 
el usuario es capaz de ejecutar en su ordenador una aplicación que realmente no está instalada en su equipo.
Un sistema de prueba de software e integración continua: Utilizaría virtualización de entornos de desarrollo ya que trata
de reproducir entornos de producción de la forma más fiel posible.


### Ejercicio 4

### Ejercicio 5 

Instala el sistema de gestión de fuentes git.

Ejecutamos desde el terminal: 

> sudo apt-get install git

### Ejercicio 6

1. Crear un proyecto y descargárselo con git. Al crearlo se marca la opción de incluir el fichero Readme.

Creo un proyecto llamado ProyectoEjercicio6 incluyendo el fichero Readme.md

Para descargarlo

> $ git clone https://github.com/melero90/ProyectoEjercicio6.git

2. Modificar el readme y subir el fichero modificado. 

Editamos readme con gedit y a continuación:

> $ git add README
> $ git commit –m 'Versión modificada del proyecto'

### Ejercicio 7

1.- Crear diferentes grupos de control sobre un sistema operativo Linux. Ejecutar en uno de ellos el navegador,
en otro un proceso de textos y en uno último cualquier otro proceso. Comparar el uso de recurso de unos y otros 
durante un tiempo determinado.

Instalamos este paquete:

> sudo apt-get install cgroup-bin

Crear un grupo que contendrá varios subgrupos. Para crearlo usamos la siguiente orden:

> sudo cgcreate -a melerob -g memory,cpu,cpuacct:pejercicio7

Este grupo se encarga de controlar la memoria, CPU y de contabilizar el uso de recursos de CPU y da permiso al usuario 
melero para que trabaje con el.

Creado el grupo, vamos a crear varios subgrupos:

> sudo cgcreate -g memory,cpu,cpuacct:ejercicio7/navegador
sudo cgcreate -g memory,cpu,cpuacct:ejercicio7/editor
sudo cgcreate -g memory,cpu,cpuacct:ejercicio7/correo

Con cgexec asignamos los procesos de cada subgrupo.

> sudo cgexec -g memory,cpu,cpuacct:ejercicio7/navegador firefox
sudo cgexec -g memory,cpu,cpuacct:ejercicio7/editor gedit
sudo cgexec -g memory,cpu,cpuacct:ejercicio7/correo thunderbird

Para comparar el uso de recursos visualizamos los resultados en:

> /sys/fs/cgroup/(memory|cpu|cpuacct)/ejercicio7/(navegador|editor|correo)


### Ejercicio 8






