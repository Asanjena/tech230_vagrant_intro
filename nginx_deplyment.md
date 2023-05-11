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



### Automating Nginx Deployment
Firstly, if you have a VM running, destroy it. Also make sure that you are in the right folder and have the corresponding vagrant file 

### Creating a provision

In the vagrant file, you can write a shell script. Vagrant will then call this and send it to the VM when it is set up

1. Create a provision.sh file in same location that your vagrant file is located
2. In line 1 of your provision.sh file, enter the following

```
~!/bin/bash
```

This says that it is a shell file
3. in the following lines, type the following: (ADD IMAGE)

```
sudo apt-get update -y

sudo apt-get upgrade -y

sudo apt-get install nginx -y

sudo systemctl start nginx
```

### Add provision

To add your provision to the vagrant file, in the vagrant file you need to add the following line:

```
config.vm.provision "shell", path: "provision.sh"
```

### Accessing the automated nginx deployment

To access, use the following steps: (ADD IMAGE)
1. in terminal, type:

```
vagrant up
```
2. Follow this with:

```
vagrant ssh
```
And you should be good to go!







### Linux and bash commands

- **touch** used to create new files 
```
    touch puppy.jpg
```
- **mv** can be used to rename a file 
```
    mv puppy.jpg puppy.txt
```
- **cat** is used to show the contents of a file/ files
```
    cat example.txt
```
- **sudo nano** edit existing file or create a new file
```
    sudo nano example2.txt
```
- **mkdir** command to create a new folder 
```
mkdir my_photos
```
- **rm** used to remove a file. state the film name after typing rm 
```
    rm puppy.txt
```
- **rm_rf** used to remove a folder. State folder name after typing rm-rf 
- **mkdir .** command to hide folder
```
 mkdir .hidden_directory
```
- **ls -al** to see all folders
- **ls -l** shows all permissions 
- **r** This means you have permission to read only
- **w** Have permission to read and write
- **x** Permission to execute/ run file
- **|** This is called a pipe. it can be used to combine commands
```
ls | head -1
```
- **tail** Will show the last part of a file
```
tail -2 
line 5
line 6
```
- **head** Will display the first part of a file
```
head -1
line 1
```
- **grep** is used to search for words
```
grep hello
```

- **top** shows you in real time the processes running and the resources being used. Use 'q' key to exit
- **ps** tells you the processes that are being run by the user
- **ps aux** more complete overview and does not lock you like top

### Making a process

Lets make a process called sleep:
```
sleep 120 &
3629
```
- The '120' part tells you the number of seconds the process will run for
- '3629' refers to the process id. Each individual process will have its own process id

- **kill** This command will kill a process
```
kill sleep 120
```
- **kill -9** This is like the 'kill' command, but more forceful
- **ctrl + z** used is a process is running and crashes. Also used to stop a process, but will not kill it
- **fg** brings backgroud processes to foreground 



## Changing permissions 
- **chmod u+x** gives the permission to execute to everyone. This is the longhand way.
```
chmod u+x example.txt
```
- **sudo chmod 777** this gives all types of permission to everyone and is a shorthand method 
```
sudo chmod 777 example.txt
```    
- **sudo chmod +x** will add permission to all users
- **sudo chmod -x** will remove permission from all users

You can use this link to check for permissions: https://chmod-calculator.com/
