# Virtual Machines

Ubuntu [likes](https://help.ubuntu.com/community/KVM) [KVM](http://www.linux-kvm.org/page/Main_Page).

1. Install a bunch of KVM packages

   ``` shell
   $ sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils virt-manager
   ```

2. Enable VM privaledges for current user:

   ``` shell
   $ sudo adduser `id -un` libvirtd
   ```

3. When (not if) you run out of volume space, your images may be found in */var/lib/libvirt/images*
   and can be grown (while the VM isn't running) with something like:

   ``` shell
   sudo qemu-img resize /var/lib/libvirt/images/ubuntu14.04.qcow2 +10G
   ```

