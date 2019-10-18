# Convert docker image to virtual machine image.

## Howto

### 1. Install libguestfs-tools

    yum install -y libguestfs-tools

### 2. Create qcow2 with docker image

    docker save instance -o vm.tar
    virt-make-fs --format=qcow2 --size=20G --type=ext4 vm.tar vm.qcow2

### 3. Import host kernel(Optional)

    tar cf kernal
    virt-tar-in -a vm.img kernel.tar /boot/

### 4. Boot with qemu

    qemu -initrd /boot/initrd.img -kernel /boot/kernel.img -append -append "root=/dev/sda"