# ESXi Ansible Provisioning

## Prerequisites

### ESXi

* Open SSH service
* Set full qualified domain name:

```bash
esxcli system hostname set --fqdn=my.esxi.host
```

### Provisioner

* Install ansible package:

```bash
sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

* Install pysphere python module:

```bash
sudo pip install pysphere
```

## Usage 

* Create Ubuntu VM:

```bash
ansible-playbook --ask-pass -i my.esxi.host, -e ansible_ssh_user=root --extra-vars "esxi_hostname=my.esxi.host esxi_datastore=my_esxi_datastore esxi_username=root esxi_password=my_esxi_password vm_guest_id=ubuntu64Guest vm_template_path=output-ubuntu-template/disk.vmdk vm_name=my_vm_name vm_cores=1 vm_ram_size=1024 vm_disk_size=10 vm_network=SZ" playbook.yml
```