# Convert virtual machine image to docker image.

## Howto

### 1. Install libguestfs-tools

    yum install -y libguestfs-tools

### 2. Export content of virtual disk

    virt-tar-out -a vm.img / vm.tar

### 3. Import tar as docker image

    docker load vm.tar vm:latest