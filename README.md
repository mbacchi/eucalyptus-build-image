## Install

### On a CentOS 7 system:

    yum install libguestfs-tools autoconf virt-install virsh virt-sysprep virt-sparsify euca2ools

## Prereqs

### libvirt/qemu configuration

    If you get permission denied errors when running 'make', you may need to modify the qemu.conf file as follows:

        sed -i.bak 's/^#user = "root"/user = "root"/' /etc/libvirt/qemu.conf
        sed -i.bak 's/^#group = "root"/group = "root"/' /etc/libvirt/qemu.conf
        systemctl restart libvirtd.service

    You would otherwise be running libvirtd as a normal user (your user id) and this runs it as root.  You might also be able to work around this by adding cgroup_device_acl as described here:

        https://libvirt.org/drvqemu.html#securityacl
