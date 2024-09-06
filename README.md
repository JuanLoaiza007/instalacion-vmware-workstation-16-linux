# Tutorial de instalación de VMware Workstation

Este es un tutorial de instalación de VMware Workstation, este método se probó en Ubuntu 22.04 LTS con una version específica de VMware Workstation.

> [!WARNING]  
> Se usa la versión de VMware Workstation 16.2.5.
>
> Cambie todas las apariciones de "16.2.5" por la versión que desee **PERO** primero revise si el repositorio de [mkubecek](https://github.com/mkubecek/vmware-host-modules/) cuenta con una rama para esta version (Ej: workstation-16.2.5), puesto a que usaremos este repositorio para instalar los módulos.

> [!WARNING]
>
> DISCLAIMER
>
> EstE tutorial se proporciona "tal cual" sin garantías de ningún tipo. No asumimos responsabilidad por daños directos, indirectos, incidentales o consecuentes que puedan surgir de su uso. Utilízalo bajo tu propio riesgo y verifica su idoneidad para tus necesidades antes de implementarlo.

## Requisitos

    sudo apt install build-essential linux-headers-$(uname -r) software-properties-common gcc g++

## Instalación de VMware Workstation

### Descarga

Descarga la versión de VMware Workstation que requiera. Puede hacerlo a través del siguiente enlace:

https://softwareupdate.vmware.com/cds/vmw-desktop/ws/

**Ejemplo de ubicacion (accediendo desde el navegador):**

    https://softwareupdate.vmware.com/cds/vmw-desktop/ws/16.2.5/20904516/linux/core/

Ahi puede hacer clic en el archivo [VMware-Workstation-16.2.5-20904516.x86_64.bundle.tar](https://softwareupdate.vmware.com/cds/vmw-desktop/ws/16.2.5/20904516/linux/core/VMware-Workstation-16.2.5-20904516.x86_64.bundle.tar) para empezar la descarga.

### Instalación de VMware Workstation

1. Descomprima el .tar

   > tar -xzf VMware-Workstation-16.2.5-20904516.x86_64.bundle.tar

2. Acceda al directorio de instalación

   > cd VMware-Workstation-16.2.5-20904516.x86_64.bundle

3. De permisos de ejecucion al archivo de instalación

   > sudo chmod 777 VMware-Installer-16.2.5-20904516.x86_64.bundle

4. Ejecuta el instalador

   > sudo ./VMware-Installer-16.2.5-20904516.x86_64.bundle

## Instalación de módulos de VMware

### Método 1: Compilar e instalar desde el código fuente

1. Descargar el archivo tarball correspondiente:

   > wget https://github.com/mkubecek/vmware-host-modules/archive/workstation-16.2.5.tar.gz

2. Descomprimir el archivo:

   > tar -xzf workstation-16.2.5.tar.gz

3. Navegar al directorio descomprimido:

   > cd vmware-host-modules-workstation-16.2.5

4. Compilar los módulos:

   > make

5. Instalar los módulos (requiere privilegios de root):
   > sudo make install

### Método 2: Reemplazar tarballs originales

1. Descargar el archivo tarball correspondiente:

   > wget https://github.com/mkubecek/vmware-host-modules/archive/workstation-16.2.5.tar.gz

2. Descomprimir el archivo:

   > tar -xzf workstation-16.2.5.tar.gz

3. Navegar al directorio descomprimido:

   > cd vmware-host-modules-workstation-16.2.5

4. Crear archivos tar para los módulos:

   > tar -cf vmmon.tar vmmon-only
   > tar -cf vmnet.tar vmnet-only

5. Copiar los archivos tar al directorio de módulos de VMware (requiere privilegios de root):

   > sudo cp -v vmmon.tar vmnet.tar /usr/lib/vmware/modules/source/

6. Ejecutar vmware-modconfig para instalar los módulos (requiere privilegios de root):
   > sudo vmware-modconfig --console --install-all

## Activación

Para activar el producto (tanto Workstation como Player) se puede usar alguna de las claves gratuitas de este repositorio:

https://gist.github.com/NSWG/2ad67111efb983c762e3425ff49ba2ad

OJO, este enlace no nos pertenece y no nos hacemos responsables de su contenido, su uso, sus implicaciones, etc.
