msr-instance-1(master)
msr-instance-2
msr-instance-1: first using ssh(secure shell connection) connect to instance2
          int-1:passwd root
                vi /etc/ssh/sshd_config
                     set permit login yes
                     passwd authentication yes
                service ssh restart
                (same in instance2)
                cd ~/.ssh
                ssh key-gen (create a key pair)
                ssh-copy-id <pubip of 2 node)  (passwd less autentication)
--------------------------------------------------------------------------------
install ansible in instance1
add anscible ppa 
#apt-add-repository ppa:ansible/ansible
#apt-get update
#apt-get install ansible
#cd etc/ansible
#vi hosts
  list the ips of slave node and check the connection using adhoc command
#ansible all -m ping
once the connection is good install packages in slave node using adhoc commands with raw module
install docker
#ansible all -m raw -a 'curl -fsfl https://test.docker.com | sh' 
install docker compose
#ansible all -m raw -a 'sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
add the execute permission
#ansible all -m raw -a 'sudo chmod +x /usr/local/bin/docker-compose'
________________________________________________________________________________
install git
#ansible all -m raw -a 'apt-get install git-core -y'
--------------------------------------------------------------------------------install node js and nvm
#ansible all -m raw -a 'curl -sL https://deb.nodesource.com/setup_8.x -o nodesource_setup.sh'

run the nodesource_setip.sh
#ansible all -m ping -a'sudo bash nodesource_setup.sh'(to add pps)
install nodejs
#apt-get install nodejs
install nvm
#ansible all -m ping -a'apt-get update'
#ansible all -m ping -a'sudo apt-get install -y build-essential libssl-dev'(fot prerequisite packages)
#ansible all -m ping -a"curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh -o install_nvm.sh'
#ansible all -m ping -a'bash install_nvm.sh'
-------------------------------------------------------------------------------------------------
open ssl
deploy targz file
#ansible all -m raw -a 'wget https://www.openssl.org/source/openssl-1.0.2-latest.tar.gz'
extract targz
#ansible all -m raw -a 'tar -zxf openssl-1.0.2-latest.tar.gz'
#ansible all -m raw -a './config'
#ansible all -m raw -a 'make'
#ansible all -m raw -a 'make test'
#ansible all -m raw -a 'make install'
#ansible all -m raw -a 'mv /usr/bin/openssl /root/'
#ansible all -m raw -a 'ln -s /usr/local/ssl/bin/openssl /usr/bin/openssl'
=============================================================================================



