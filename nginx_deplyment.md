### Nginx deployment using vagrant

### Vagrant Up
1. In the VScode file,  removing everything but leave the 4 lines: ( vagrant. configure, config.vm.box, config.vm. network, and end).
2. The config.vm.box line will usually be followed by = "base". Swap "base" for "ubuntu/xenial64". For example - config.vm.box = "ubuntu/xenial64"
3. Once you have completed this, in the terminal enter: vagrant up
4. To then enter the linux virtual machine (VM), in the bash terminal type: vagrant ssh. This should return your username in green. 

### Update
1. In the terminal, type: sudo apt-get update. This will grab the updates for you but will not implement them just yet.

### Upgrade
1. To put into effect all the latest updates and start using them, in the terminal type: sudo apt-get upgrade -y. The -y helps to automate the process by confirming that you want to go ahead. You have to be careful when upgrading as it will now make the changes. 

Afte this, you can type: clear in the terminal to remove all the outputs from the terminal. 

### Installing and starting Nginx
1. In the terminal, type: sudo apt-get install nginx -y
2. Follow this with: sudo systemctl start nginx (in terminal)
3. Next, type: sudo systemctl status nginx (in terminal), to get the status

### Acessing the nginx webserver 
1. In the file, for the config.vm.network line, add "private network" followed by your ip address. For example - config.vm.network "private_network", ip:"192.168.10.100"
2. Exit VM by typing: exit, in the terminal
3. To implement instructions enetered in the file, type: Vagrant reload 
4. Copy the ip address into a web browser to access your web server.