Como Compilar El Kernel Zen En Linux de Cero a Femboy

sudo dnf install patch wget gcc ncurses-devel git git-core flex bison openssl-devel dwarves openssl elfutils-libelf-devel lz4 zstd

sudo dnf groupinstall "Development Tools"

git clone --depth 1 https://github.com/zen-kernel/zen-kernel.git 

mkdir kernel
mv zen-kernel/ kernel

cd /boot

ls -a

cp config-5.7.7-200.fc32.x86_64 /home/YOURNAME/kernel/zen-kernel/.config

cd /home/YOURNAME/kernel/zen-kernel/

make oldconfig

make menuconfig

make -j8

sudo make modules_install install


OPCIONAL POR SI DA ERRROR   
make clean && mrproper

[![ZEN.jpg](https://i.postimg.cc/brcjdM07/ZEN.jpg)](https://postimg.cc/YG3PsdsR)
