# Virtual Machine - New Virtual Machine
## VIRTUAL MACHINE - CREATE NEW VIRTUAL MACHINE [Virtual Machine Manager]

- Create a new directory for the VM
  ```
  sudo mkdir ~/Documents/KVM
  ```
- Destroy the default storage pool
  ```
  sudo virsh pool-destroy default
  ```
- Undefine default storage pool
  ```
  sudo virsh pool-undefine default
  ```
- Setup default storage pool
  ```
  sudo virsh pool-define-as --name default --type dir --target ~/Documents/KVM
  sudo virsh pool-autostart default
  sudo virsh pool-start default
  sudo virsh net-autostart default
  sudo virsh net-start default
  ```
- Download the ISO of the OS
- Move your OS ISO image into `~/Documents/KVM`
- Open `Virtual Machine Manager`
	- Create a new virtual machine `Change the values for your needs`
		- Choose your ISO image
    		- Memory: 32000
    		- CPUs: 16
    		- Customize configuration before install
  	- Overview
    		- Firmware: UEFI x86_64 /usr/share/edk2-ovmf/x64/OVMF_CODE.fd
  	- Boot Options
	  	- Enable boot menu
	  	- Select SATA CDROM & put it first
  	- Remove Tablet, Display Spice, Channel spice, Video QXL, USB Redirector 1 & 2
  	- Add PCI Host Device (GPU) `Use your GPU PCI buses`  
    		- 0000:12:00.0  
    		- 0000:12:00.1  
    		- 0000:12:00.2  
    		- 0000:12:00.3
	- Add PCI Host Device (Network interface port) (optional) `Use your Network interface PCI buses`
		- 0000:08:00.0
	- Add PCI Host Device (USB hub) (optional) `Use your USB hub PCI buses`
		- 0000:06:00.0
		- Remove the Virtual Network Interface
