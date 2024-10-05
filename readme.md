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

------------------------------------------------------Continue----------------------------------------------------------------

# Devops

- [python and GO[recommended]]

# Prequisite ::
- Need before starting
    1. Shell Scripting  [shell commands]
    2. Networking
        - Ports
        - TCP
        - UDP
        - ID add
        - Subnet
        - Domain and subDomain
        - OSI model [7- layer of networking]
    3. Git 
    4. Application Development Framework 

# Devops syllabus:
- 
    - CI CD alternative Jenkins
    - Dockers = deploy application through docker
    - containerization
    - Kubernetes
    - Monitoring of wevservers
    - best practises

- Doing some task repetatively [automation tool]
    - cronjob[linux] = every 30 minutes/week/monday run this file for me
    - Jenkins = do same above work more better job with even complex task
    - schedulejob



# Developer VS OPs[IT-operations person]

- Devops take care of collaboration and communication of both developer and OPs teams. It is not the combination of developer and ops.
- It is basically a connecting point of both the things.

- Developers Responsibility
    - Write code 
    - Tests the code [unit and Integration] 
    - Design the App [HLD,LLD] 
    - Source control Management 
    - Compile the code 

- Devops Responsibility
    - Manage and provision Environments
        - production-environment is a group of machines ie fe,be,db,loadbalancer, middleware, caching, queue, notification service and lot of it
    - User access and premission.[UAT-user acceptance testing]
    - Configuration Management [ENV variable]
    - Dependency Management [packages]

- Before Devops:
    - Waterfall methods is used.[which includes]
        1. Planning/Requirement
        2. Design
        3. Development
        4. Testing
        5. Deployment
        6. Maintenance
        - Cons:
            - if test have bugs then start from 1 again.
            - Each step is initialised in chronological manner.
            - Next step is only started once above is completed.
            - Takes a very long time 
    
    - Agile methods .[which includes]
        1. Planning/Requirement
        2. Design
        3. Development
        4. Release
        5. testing
        - Monthly sprint repeat same steps, if bug are there.

    - Devops:
        - Taking feedback at every steps [design,develop,deploye]:
        - Three major/core principles of devops:
            1. Continuous Integration
            2. Continuous Delivery
            3. Continuous Deployment
        - Automation + collaboration + measurement(moniter).
        - 
            1. Continuous Integration:
                - when code is push to git after completion it automatically get build [in node there is no build option however GULP is used but in Java and go there is built option available.] and run some unit test cases and it run some integration test and store some compiled code as a package so that is CI.

                - CI says code should always be in a deployable stage in production environment.[Highquality code]

                - once the code is git now it is the work of jenkins tools where automated testing is done.

            2. Continuous Deployement means how it will reach the production. we automate the whole deployment method to production without any manual intervention.

            - IT rolls out the new feature without any downtime.

        - Pros:
            - Less or no downtime
            - Improved deployment frequency by continuous deployement [1week/3/6months deployement cycle] without waiting for the release.
            - Lower failure rate of new releases.
            - Shorter lead time b/w error fixes.
            - Enhance collaboration, teams will be happy other wise keep fighting.

- also see diffrence b/w agile method and devops culture.

# Devops lifecycle [SDLC and SDLC-devops];

- Steps:
    1. Planning [along with HLD]
    2. Design and develop goes side by side. [Design and develops the API]
    3. Continuous Integration [Testing]
        3.1 continuous Delivery [middle-process]
    4. Continuous Deployment.
    5. Continuous Monitoring. [eg Promethesus]
    6. Continuous Feedback.
    7. Continuous Inprovement.

- Above steps are not predefined boudaries as the steps can overlap. Think of it as a pipeline. so when the compilation is done using CI it is deployed in a stage environment and not in the production and then comes the user acceptance


- Flow = code/IDE >> Github >> build/compile >> unit testing
                    build/compile >> storage

- CI start from Github till unit-testing.

1. Continuous Integration
    -  compilation is done using CI after which is it is deployed in a stage environment 
    - Tools for CI:
        1. Travis CI
        2. Circle CI
        3. Jenkins [for integration, deployment and delivery also]

    - Outcome of CI is unified code base that is continously updated and tested ensuring stability.

2. Stage environment = It is a Replica of production. Contains dependency , packages.

3. Continuous Deployment: stage to production env
    - Help in implementing varous Rollout stratigies.
    - Also gives the feature of rollback.
    - Tools = Kubernetes, Docker, Argo CD, AB rollouts or blue-green deployment.

    - Rollout Statigies:
    1. Kanary 

4. Continuous Monitoring:
    - eg promethesus.
    - collect the data/metric of the cpu usage and upload on promethesus server.
    - GUI is Graffana to show the data in pie chart or any other chart
    - Promethesus is a real time monitoring tool that gather the data and Graffana help in visual appreance of the data through GUI
    - it also have alertsytem to track unusual behhaviour based on our configuration.
    - Another tool - Elasticsearch logstach kibana ELK
        - EL collect data and Kibana is GUI.
    - Other tools = Survey monkey and newRelic.

- Production is done on multiple servers. same code runs of all the instances. but incase of new feature it is installed in one server and if it works well then it is intalled in all the server.


- Artifact = 
    - Packaged application/compressed code /compiled code.
    - so with the help of artifact it can be run.
        - c++ and golang and python, shell, docker no need of build
        - java and JS requires build
    
- storage can be aws s3, 

# Basic Tools Info
- Agile-methods of SDLC
    - Tools :: Kanban/sprint board OR Jira board/tickets[majorly-used] OR Trello [free]::
        - Boards have 3 parts:
            left = Todo plan
            middle = ongoing/doing
            right = complete/done

- Jira is like azure.
- Jira is a project management tool.
- Jira ticket is basically a task
- Also can Integrate the customer service.

- Unit testing Tools:
    - java = Junit tesing
    - JS = selenium based [mocha, chai], JEST framework for testing 

- Developement tools:
    - IDEs = Vscode, intellij,
    - Version control = Git

## IAAC - Infrastructure as a code [cloud]:

- TO write complete infrastructure/code in a single file. which has all the services,configuration etc.
- so as to Transfer/migrate complete Infrastructure from one cloud to another cloud.
- Terraform help in this process becoz different clouds have different configuration need.

## Cloud Providers:

- Cloud providers : AWS, Azure, GCP, Heroku
- Storage, Network connectivity, Backup = to overcome all these issue cloud provider are used.
- They provide remote server and very highperforming with huge datacentres, encryption, highavailability, power alltime, disaster recovery, remote access.

## Docker

- It is containerization tool and not a virtual machine
- Docker first create the virtual Machine and then create a all the container in that VM.

- Virtual Machine [VM]
    - VMware used to create a virtual OS environtment such as linux, windows, ubuntu, centos. 
    - Linux basically have images for free of cost and these images are complete OS actually which we can install in the machine to use that particulat OS in any OS
    - Virtual Machine = secondary OS kerner>>Hypervisor>>OS kerner[window] >> Hardware
    - Cons:
        if we give 4 core/thred assigned to this new OS then it will occupy the 4 Core even if it is not running and the rest 4 can be given to some other OS
        incase we want to have more than 2 OS in the machine then it will create a issue therefore to overcome this issue we will use containers

- Container:
    - They are wrapper over a process but not a smaller version of VM.
    - This wrapper is actually a container which is flexible interms of core only take the those core which are required and not n number always
    - eg suppose if a windows has linux VM which has a docker container, now if a application requires a window then the linux will again create a windows VM inside a linux VM so this wont happen in case docker becoz in docker we have to config whether we want to run in windows or the linux mode
    - Images is the snapshot of the OS, it create a backup and create a litte compressed form. so we can access it later in the origin form even after long time.
    - Image cannot be accessed until it is not mounted to any hardware.



## Setup devops environt

- setup 
    - Jenkins with docker, jenkin with server, jenkin with java17 [jenkins-have-java-dependency]
        - https://www.oracle.com/in/java/technologies/downloads/#jdk17-windows
    - AWS account with bill [alter if cost money] 
    - Git or Gitbash [more interactive]
    - Docker
- 