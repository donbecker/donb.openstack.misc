* select language english
* select date/time phoenix
* click done
* click installation destination
* click done
* click network & host name
* set hostname to `openstacktest`
* click apply
* click the ON button to enable networking
* verify DHCP retrieves IPv4, etc
* click configure
* click ipv4 settings
* click method and change to manual
* under addresses, click add
* add static ipv4, netmask and gateway
* enter dns servers, click save
* click done in network
* click date & time
* verify ntp showing as on
* click ntp settings icon 
* verify all are green
* click done on date & time
* click begin installation
* while install continues
    * set password for root: toortoor
    * create user
        * name "centos"
	* pass sotnecsotnec
        * check "Make this user administrator"
* after install completes, click reboot
* ssh to centos vm directly using IP, "trilliams" user and password
* perm elevate to sudo 
    * `sudo -i`
* update via yum 
    * `yum -y update`
* install packages
    * `yum -y install centos-release-qemu-ev`
* remove existing mariadb libs
    * `yum -y remove mariadb-libs`
* elevate normal user to be able to run sudo commands without prompt
    * `visudo`
    * uncomment
        * `%wheel ALL=(ALL)         NOPASSWD: ALL`
    * save file
* disable SE Linux
    * `vi /etc/selinux/config`
    * change 
        * `SELINUX=enforcing`
        * to
        * `SELINUX=disabled`
    * save file
* disable network manager and firewalld
    * `systemctl disable NetworkManager firewalld`
* reboot server to make all changes take affect
* list versions of openstack
    * `yum search openstack`
* install openstack repos via yum
    * `sudo yum -y install centos-release-openstack-ocata`    
* install packstack
    * `sudo yum -y install openstack-packstack`
* generate answerfile
    * `packstack --gen-answer-file=/home/centos/answers.txt`
* update answers file 
    * `vi answers.txt`
* run packstack
    * `packstack --answer-file=/home/centos/answers.txt`