# Linux:

## Linux cli
## Vi Editor
## Package Management
## Service Management

## Linux cli [Prefer-CentOS]

- It is CentOS, Ubuntu, RHEL, Suse, Debian,kai
- Linux has both CLI and GUI.
- We need shell to interact with the CLI
- Types of Shell:
    1. Bourne Shell [SH-Shell]
    2. C Shell [csh/tcsh]
    3. Z shell [zsh]
    4. Bourne Again Shell [BASH]

- echo $shell :
    - $ is for the environment variable
    - echo means print

## Part-1
- echo $shell = To kown which shell you are using
- ls = list all directory
- cd <filename> = navigate to new directory
- pwd = present working directory
- mkdir <filenave> = to create new directory
- cd .. or cd ../ = to go back into the directory
- cmd1; cmd2; com-n = to run multiple commands in one-go use semicolon.
- mkdir -p /<dir-name>/<dir-name>/<dir-name> = to create multiple directory in one go other have to run the command again and agian.
- rm -r /<dirname>/<dirname> = to remove all directory along with the content
- cp -r <my-dir> /<dirname>/<dirname> = to make of copy of directory along with content in some other directory
- touch <filename.md> = to create a new file [without content]
- cat > <filename.md> = to write in file. [promt will appear to write the content]
    - to exit writing = Ctrl + D
- cat <filename.md> = to read the file [no ">" symbol]
- cp <newfile.txt> <copyfile.txt> = to copy a file
- mv <newfile.txt> <copyfile.txt> = to move [rename] a file
- rm <newfile.txt> = to remomve a file.

## Part-2
- whoami = to know the user
- id = to know the userid and groupid
- su <username> = to switch user
- ssh <username>@<IP-addres> = to access another remote system through your system
- 

- Linux has two users:
    - Super/root user [admin]
    - Regural user = some permisssion restricted

    - Super/root user:
        - installtion/config/services software
        - can view root directory
        - ls =o/p=> /root
    - Root user grant the regular user to use above thing by granting "SUDO Privilege"
        - sudo ls =o/p=> /root

-  To Download file from internet such as rpm package,binary fiile,
    - curl <link/<filename.txt>> -O = one way
    - wget <link/<filename.txt>> -O <filename.txt> = 2nd way

- TO check OS version
    - ls /etc/*release*
    - cat /etc/*release* = more detailed

## Package manager

- npm install <packagename> / rpm i <packagename.rpm> = install package

- rpm -e <packagename.rpm> = uninstall package
- rpm -q <packagename.rpm> = query package

## services in Linux

- help configure services such as webservers, dbservers,docker.
- on reboot the services should automatically restart
- and in the correct order.
- so when [webservers, dbservers,docker] are install in the linux system they are automatically considered as services.

- systemctl = system cuddle

* Commands
- service <servicename> start or systemctl start <servicename>  = start service
- systemctl stop <servicename> = stop service
- systemctl status <servicename> = check service status
- systemctl enable <servicename> = configure service to start at startup
- systemctl disable <servicename> = configure service not to start at startup

### systemd services
- /etc/systemd/system = location of systemd files[doubt]
- To run application as services run below commands:
    my_app.service
    [Service]
    ExecStart=/usr/bin/python3/opt/code/my_app.py
    systemctl daemon-reload
    systemctl start my_app

- TO check the working = curl http://localhost5000
- TO stop the service = systemctl stop my_app