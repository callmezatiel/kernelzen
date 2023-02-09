<h1 align="center">
  <br>
  <a href="https://github.com/callmezatiel"><img src="https://i.postimg.cc/qMmnw0b4/zenk.png" width=320 height=300 alt="Guia Completa"></a>
  <br>
  Guia Completa
  <br>
</h1>

## Como Compilar El Kernel Zen En Linux de Cero

### 1.- Solucionar las dependencias de el sistema
```
sudo dnf install patch wget gcc ncurses-devel git git-core flex bison openssl-devel dwarves openssl elfutils-libelf-devel lz4 zstd
```
Utilizar "apt" "pacman" "dnf" segun sea el caso

### 2.- Instalar paquetes de desarrollo dependiendo del sistema⚠️

| Distro| Comando a utilizar |
| ------ | ------ |
| Ubuntu / Debian | sudo apt-get install build-essential |
| Open SUSE |  sudo zypper install --type pattern devel_basis |
|Fedora|sudo dnf groupinstall "Development Tools"|
|Arch Linux | No es necesario ya que al momento de instalacion del kernel base, se instalan de manera indirecta|


### 3.- Clonar el Kernel Zen del repositorio oficial con el sigueinte comando
```
git clone --depth 1 https://github.com/zen-kernel/zen-kernel.git 
```
### 4.- Crear una carpeta y mover la carpeta descargada a la recien creada 
```
mkdir kernel
```
```
mv zen-kernel/ kernel
```
### 5.- Cambiar al directorio /boot para verificar la configuracion del kernel anterior y hacer una copia para evitar rellenar casillas
```
cd /boot
```
```
ls -a
```
### 6.- Hacer una copia del archivo config
* El archivo config es diferente para todos pero se necesita seguir la sigueinte estructura de comando

```
cp config-5.17-300.fc36.x86_64 /home/YOURNAME/kernel/zen-kernel/.config
```
```
cd /home/$USER/kernel/zen-kernel/
```
* $USER (variable de entorno) es igual a tu nombre de usuario, se puede consultar con el comando "whoami" en cualquier terminal y sustituir la palabra
### 7.- Establecer la configuracion en base a la anterior 
```
make oldconfig
```
### 8.- Setear y confirmar los datos seleccionados
```
make menuconfig
```
### 9.- utilizar el comando nproc para verificar la cantidad de cores disponibles deacuerdo a tu procesador (todos tenemos un valor diferente
```
nproc 
```
### 10.- Comenzar el proceso de compilacion, 
* En mi caso deacuerdo al comando anterior mi valor es 8 pero es a consideracion tuya (vease tutorial)
```
make -j8
```
### 11.- Establecer los modulos de arranque y exportar los ajustes finales
```
sudo make modules_install install
```
### Comando alternativo por si se decea reanudar el proceso de compilacion y da error, reanudar desde el paso 10   
```
make clean && mrproper
```
* En caso de no entrar directo al nuevo kernel, precionar la tecla "Esc" en el booteo para omitir el plymouth, o entrar mediante "opciones avanzadas" dependiendo del sistema

### Visita el tutorial para mas detalles
[![Alt text](https://i.postimg.cc/xTJkYHjN/zen.png)](https://www.youtube.com/watch?v=6ZYu_lNvLUo)

###  💙 Agradecimiento y creditos
Zen Kernel Documentation

### Autor
Zatiel ([callmezatiel](https://github.com/callmezatiel))

### Issues will be fixed asap. Pull Request Welcomed
https://github.com/callmezatiel/kernelzen/issues

### Buy me a coffee
<a href="https://www.paypal.me/zatiel"><img src="https://img.shields.io/badge/don-paypal-blue"></a> <a href="https://www.patreon.com/zatiel"><img src="https://img.shields.io/badge/don-patreon-ff69b4">

