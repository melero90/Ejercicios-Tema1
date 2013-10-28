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

> sudo cgcreate -a melerob -g memory,cpu,cpuacct:ej7

Este grupo se encarga de controlar la memoria, CPU y de contabilizar el uso de recursos de CPU y da permiso al usuario 
melero para que trabaje con el.

Creado el grupo, vamos a crear varios subgrupos:

> sudo cgcreate -g memory,cpu,cpuacct:ej7/nav
sudo cgcreate -g memory,cpu,cpuacct:ej7/edit
sudo cgcreate -g memory,cpu,cpuacct:ej7/mail

Con cgexec asignamos los procesos de cada subgrupo.

> sudo cgexec -g memory,cpu,cpuacct:ej7/nav firefox
sudo cgexec -g memory,cpu,cpuacct:ej7/edit gedit
sudo cgexec -g memory,cpu,cpuacct:ej7/mail thunderbird

Para comparar el uso de recursos visualizamos los resultados en:

> /sys/fs/cgroup/(memory|cpu|cpuacct)/ej7/(nav|edit|mail)

Vemos los resultados.


### Ejercicio 9

Comprobar si el procesador o procesadores instalados lo tienen. ¿Qué modelo de procesador es? ¿Qué aparece como salida 
de esa orden?.

> egrep '^flags.*(vmx|svm)' /proc/cpuinfo

Resultado: flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr 
sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 
ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 
ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 
xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority

Mi procesador es un Intel Core Centrino2 a 2,26Ghz.


### Ejercicio 10

Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok.

Ejecutamos en la terminal:

> kvm-ok

Resultado:

> INFO: /dev/kvm exists
KVM acceleration can be used

### Ejercicio 11

Comentar diferentes soluciones de Software as a Service de uso habitual.

> El Saas que uso de manera muy habitual son GMail. 

### Ejercicio 12

Instalar un entorno virtual para tu lenguaje de programación favorito (uno de los mencionados arriba, obviamente).
El entorno virtual que he instalado ha sido virtualenv para Python. El motivo es porque es un lenguaje que estoy 
aprendiendo en una de las asginaturas de este curso.

> $ sudo pip install virtualenv

Previamente he tenido que instalar pip. La forma de usarlo y activarlo es la siguiente:

> $ virtualenv ENV
> $ source bin/activate


### Ejercicio 13

Darse de alta en algún servicio PaaS tal como Heroku, Nodejitsu u OpenShift.

Me he dado de alta en OpenShift y lo he utilizado posteriormente para la realización de la práctica 1.

> Debemos acceder a la web:https://www.openshift.com/ y darnos de alta insertando el correo electronico,una contraseña 
de acceso a la plataforma y algún dato más.







