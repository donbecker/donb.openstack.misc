esxi1-esxi 6.5 install

#hostname
r7103openstack

# ipv4
192.168.1.111

# dns servers
192.168.1.10

# post reboot

# search for openstack version
yum search openstack

# install latest, rocky
sudo yum -y install centos-release-openstack-rocky

# install packstack
sudo yum -y install openstack-packstack

# install iotop
sudo yum -y install iotop

* update answers file 
    * `vi answers.txt`
CONFIG_DEFAULT_PASSWORD=pass
CONFIG_HEAT_INSTALL=y
CONFIG_MAGNUM_INSTALL=y
CONFIG_TROVE_INSTALL=y
CONFIG_IRONIC_INSTALL=y
CONFIG_KEYSTONE_ADMIN_USERNAME=keystoneadmin
CONFIG_KEYSTONE_ADMIN_PW=pass
CONFIG_KEYSTONE_DEMO_PW=pass

* run packstack with large timeout
    * `packstack --answer-file=/home/centos/answers.txt --timeout=0`