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



## Customizing Vgrantfile
Customizing Vgrantfile for 
1) Static IP uncommnet line with  config.vm.network and assign IP e.g 192.168.56.14
```
 # Create a private network, which allows host-only access to the machine
 # using a specific IP.
   config.vm.network "private_network", ip: "192.168.56.14"
```

2) Bridged network
```
  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
   config.vm.network "public_network"
```

3) Customize CPU and Memory  
Customised block should look like
```
   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "1500"
     vb.cpus = "1"
   end
```
4) Shared folder configuration
```
  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
    config.vm.synced_folder "H:\\VirtualBox-VMs\\vagrant-vms\\data\\centos-data", "/opt/vagrant_data"
```
- Provisioning VM/Executing commands & scripts