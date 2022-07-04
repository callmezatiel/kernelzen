<h1 align="center">
  <br>
  <a href="https://github.com/callmezatiel"><img src="https://i.postimg.cc/qMmnw0b4/zenk.png" width=160 height=150 alt="Guia Completa"></a>
  <br>
  Guia completa
  <br>
</h1>

## Como Compilar El Kernel Zen En Linux de Cero

### Paso 1.- Solucionar las dependencias de el sistema

sudo dnf install patch wget gcc ncurses-devel git git-core flex bison openssl-devel dwarves openssl elfutils-libelf-devel lz4 zstd


### 2.- Instalar paquetes de desarrollo dependiendo del sistema

Ubuntu / Debian: 
sudo apt-get install build-essential

Open SUSE:
sudo zypper install --type pattern devel_basis

Fedora:
sudo dnf groupinstall "Development Tools"

Arch Linux
No es necesario ya que al momento de instalacion del kernel base, se instalan de manera indirecta

### 3.- Clonar el Kernel Zen Del repositorio oficial con el sigueinte comando

git clone --depth 1 https://github.com/zen-kernel/zen-kernel.git 

### 4.- Crear una carpeta y mover la carpeta descargada a la recien creada 
mkdir kernel
mv zen-kernel/ kernel

### 5.- Cambiar al directorio /boot para verificar la configuracion del kernel anterior y hacer una copia para evitar rellenar casillas
cd /boot
ls -a

### 6.- Hacer una copia del archivo config
###NOTA: El archivo config es diferente para todos pero se necesita seguir la sigueinte estructura de comando:
cp config-5.7.7-200.fc32.x86_64 /home/YOURNAME/kernel/zen-kernel/.config
cd /home/YOURNAME/kernel/zen-kernel/

### 7.- Establecer la configuracion en base a la anterior 
make oldconfig

### 8.- Setear y confirmar los datos seleccionados
make menuconfig

### 9.- utilizar el comando nproc para verificar la cantidad de cores disponibles deacuerdo a tu procesador (todos tenemos un valor diferente
nproc 

### 10.- Comenzar el proceso de compilacion, en mi caso deacuerdo al comando anterior mi valor es 8 pero es a consideracion tuya (vease tutorial)
make -j8

### 11.- Establecer los modulos de arranque y exportar los ajustes finales
sudo make modules_install install

## Comando alternativo por si se decea reanudar el proceso de compilacion y da error, reanudar desde el paso 10   
make clean && mrproper

[![ZEN.jpg](https://i.postimg.cc/brcjdM07/ZEN.jpg)](https://postimg.cc/YG3PsdsR)
