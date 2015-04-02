notes-openstack
===============

#### Install QEMU
```sh
sudo apt-get install qemu-system qemu-utils
```

#### Create an Image with QEMU
```sh
qemu-img create -f qcow2 <image_name>.qcow2 10G
```

#### Convert an Image with QEMU
```sh
# Convert from vdi to qcow2
qemu-img convert -f vdi -O qcow2 ubuntu.vdi ubuntu.qcow2
```

#### Nova Commands
```sh
nova list # List Servers

```

#### Neutron Commands
```sh
neutron net-list # List Networks
```

--
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">notes-openstack</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://jim-beaudoin.com" property="cc:attributionName" rel="cc:attributionURL">Jimmy Beaudoin</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
