## For ease of use you can add ssh verifikation keys so no password prompt is needed

 # Add user ansible to the destination server 

    sudo useradd -m -s /bin/bash ansible
    sudo passwd ansible


  Give the user sudo Perms

    sudo usermod -aG sudo ansible
      
   *when using CentOS oder RHEL*
      
    sudo usermod -aG wheel ansible

  Optionaly you can grand authless sudo perms 

    sudo visudo
    ansible ALL=(ALL) NOPASSWD:ALL

  Test User

    sudo whoami


 # Create SSH Keys on the Ansible server 

    ssh-keygen -t rsa -b 4096 -C "ansible@yourserver"
      
  *the keys will be safed in ~/.ssh/id_rsa (private) ~/.ssh/id_rsa.pub (public)*

  Send the Public key to the destination server 

    ssh-copy-id ansible@destserver

  Test Out the connection 

    ssh ansible@destserver


