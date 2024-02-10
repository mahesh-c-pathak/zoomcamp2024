# Readme

### Setting up the environment on cloud VM

* Generating SSH keys
  ---
  https://cloud.google.com/compute/docs/connect/create-ssh-keys
  
   ssh-keygen -t rsa -f ~/.ssh/gcp -C mahesh -b 2048
  
  ---
* Creating a virtual machine on GCP
  ---
  4 core 30GB disk
  
  ---
* Connecting to the VM with SSH
  ---
  
  ssh -i ~/.ssh/gcp mahesh@34.125.239.148
  
  ---
* Installing Anaconda
  ---
  wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh

  bash Anaconda3-2023.09-0-Linux-x86_64.sh
  
  ---
* Installing Docker
  ---
  sudo apt-get update
  
  sudo apt-get install docker.io
  
  ---
* Creating SSH `config` file
  ---
  c/Users/Mahesh/.ssh
  nano config
  Host "vm-instance-name"
    HostName "external IP"
    User mahesh
    IdentityFile ~/.ssh/gcp

  ssh "vm-instance-name"

  ---
  
* Accessing the remote machine with VS Code and SSH remote
  ---
    vs code extension remote-ssh enable

  In VS Code, select Remote-SSH: Connect to Host... from the Command Palette (F1, Ctrl+Shift+P) 
   and use the same user@hostname as in step 1.
  
  ---
* Installing docker-compose
  ---
  wget https://github.com/docker/compose/releases/download/v2.24.4/docker-compose-linux-x86_64 -O docker-compose
  
  chmod +x docker-compose
  
  ./docker-compose version

  in .bashrc update

  export PATH="${HOME}/bin:${PATH}"

  source .bashrc
  
  ---
* Installing pgcli
  ---
  pip install pgcli

  conda install -c conda-forge pgcli
   pip install -U mycli

  pgcli -h localhost -p 5432 -u root -d ny_taxi

  pgcli -h localhost -u root -d ny_taxi
  
  ---
* Port-forwarding with VS code: connecting to pgAdmin and Jupyter from the local computer
 in vs code forward port

* Installing Terraform
---
  wget https://releases.hashicorp.com/terraform/1.1.7/terraform_1.1.7_linux_amd64.zip

  sudo apt-get install unzip

  unzip terraform_1.1.7_linux_amd64.zip

  terraform -v

  create service account :- terraform_runner

  service accunt --manage keys --- add key--- json

  terraform fmt
  terraform init
  terraform plan
  terraform apply

---
* Using `sftp` for putting the credentials to the remote machine
---
    sftp de-zoomcamp

    mkdir .gc

    cd .gc

    put my_cred.json

---
* Shutting down and removing the instance
