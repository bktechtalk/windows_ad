# windows_ad
Create a window ad with ansible roles
=======================================
Configure Ansible Controller node to have connectivity from windows machine.
============================================================================
1. Install PIP, if pip is not already installed then first configure eple repo and configure PIP 
a)	Install “epel-release-latest-7.noarch.rpm” 
# wget http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
# rpm -ivh epel-release-latest-7.noarch.rpm
2)	Install pip using yum 
# yum -y install python-pip
3)	Now install “pywinrm”
# pip install "pywinrm>=0.2.2"


Create a Inventory file for windows 
=================================
# cat inventory
[windows]
## These are the activedirectory servers
ad1.internal ssh_host=ad1.example.opentlc.com

[windows:vars]
ansible_connection=winrm
ansible_user=Administrator
ansible_winrm_server_cert_validation=ignore
ansible_password=redhat@123
ansible_become=false

===================================
Test the connectivity from controller machine to Window
=======================================================
#ansible windows -m win_ping
[root@bastion ~]# ansible windows -m win_ping
ad1.internal | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
[root@bastion ~]#



