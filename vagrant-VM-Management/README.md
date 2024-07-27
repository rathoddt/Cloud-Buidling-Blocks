# VM Managemnt using Vagrant
- VM changes automatic through Vagrantfile
- Vagrant Insttalllation
Install chocolatey from URL 
https://docs.chocolatey.org/en-us/choco/setup/
or run Powershell command using admin priviledges
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Install Vagrant using choco command
```
choco install vagrant --version=2.4.1 -y
```

- Vagrant commands to manage VM’s
```
# Install/start VM
vagrant up
# Remote login 
vagrant ssh 

# Stop VM
vagrant halt

# Delete VM
vagrant destroy
```

1. Create directory
   - Create directory to store vagrant files e.g. `vagrant-vms`
2. Download VM image
   - Downlaod VM image from vagrant cloud `https://app.vagrantup.com/`
   ```
   vagrant init eurolinux-vagrant/centos-stream-9
   ```
   A `Vagrantfile` has been placed in this directory. You are now ready to `vagrant up` your first virtual environment! Please read the comments in the Vagrantfile as well as documentation on `vagrantup.com` for more information on using Vagrant.

   ```
   vagrant up
   vagrant list
   vagrant status

   #Inside VM
   uname -m
   cat /etc/os-release
   whoami
   sudo -i  #login to root user

   vagrant halt
   vagrant reload #reload
   vagrant global-status # for all vms 
   ```







- Provisioning VM/Executing commands & scripts