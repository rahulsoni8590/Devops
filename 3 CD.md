# Continuous deployment

- For CD the code should of highest quality so that it is always deployable stage.


# AWS:

- IT has two user
    1. root user
    2. regular/admin user 

- keep root user as safe and use the regular user

// alternative of jenkins = [TeamCity,AWSCodePipeline,Bamboo,CircleCI.]
// alternative of docker is podman


- Create a new user ie the regular user
    - Groups
        - Group have permission defined so any one added to the group will have all the permission so dont need to define the permission of each user.

- Now Signin as IAM user.

# Creating EC2 Instance:

- EC@ is like a virtual server running on cloud.
- It is an instance. It works like a OS in which we can install softwares.


- username = ec2-user 
    - click on connect to know the username for the instance becoz name is different
- keypair name = EC2Creds

- create the EC@ instance.
- Once connect the instance it will open the terminal or use the below command in windows
- in Terminal = ssh -i ./GIVEPATHofPEM username@ public IPv4 ADDRESS or  public IPv4 DNS
    eg : ssh -i .\Downloads\EC2Creds.pem ec2-user@3.110.222.230

-  sudo yum install -y nodejs
-  sudo npm install -g pm2
-  sudo mkdir -p /var/www/html
-  cd /var/www/html
- sudo yum install git
- sudo chown ec2-user:ec2-user html [go in html to change ownership from root to IAM user]
-  git clone https:rep . = "." will install it in the current folder [html] not create a folder that is in the repo url.
- rm -r folder-name = to remove folder
- ls -ltr = to check total number of content/files/folder inside current directory
- npm install = to install project dependency
- pm2 start server.js = to start server
- npm start = to start the server
-  diff in npm and pm2 is that pm2 will keep the server running even if the terminal is closed 
- vi server.js = to check port number >> to exit ":qa! + ENTER"
- pm2 stop <application_name> = to stop server

- to check the application 
    - also give access to the port in the security tab in the instance.
        - click security tab >> click security group >> inbound rules > add custom port >> save rules.
    - to go ipv4 address or the dns eg :port number
    - remove the https to http on click of dns:port.

- Go to jenkin, there are two ways to connect to machine
    1. by ssh cli command
    2. go to manage jenkins >> Nodes >> addNewNode >> 
        node name >> Permanent agent >> create >> remote root directory ["/home/ec2-user"- do "cd ~ and then pwd" or "echo $home"] >> launch via ssh [host - public ipv4 address , create credential >> host key verification strategy - keep 'non verifying verification strategy' >> ssh-username-with-privatekey>>id[any]>>username[any]>>privatekey>>enter directly [copy-paste pem file]]>>Disk Space Monitoring Thresholds [put 200 MiB] >> save
    3. install ' sudo yum install java-17-amazon-corretto' on ec2 terminal
    4. ' /usr/bin/jvm/java-17-amazon-corretto/bin/java'
    5. create new pipeline with
     with agent as ec2node we created above:: [    
        pipeline{
            agent {
                node {
                    label 'ec2-Node'
                }
            }

            stages{
                stage('Deploy to prod'){
                    steps{
                        sh 'echo Hellow'
                    }
                }
            }
        }
        ]



# Deployment Stratagies:
- v1 and v2 are cluster of different machines.
- Recreate Deployment:
    - Defi : If there two version v1 and v2 and we want to deploy new version we get rid of v1 and deploy v2
    - pros : easy to setup, application state entirely renewed,
    - cons : Downtime

- Blue-Green Deployment:[maybe]
    - Defi : If there two version v1 and v2 and we want to deploy new version , so one is working and another one is idle. after testing v2 is deployed and v1 is updated to v2 version code and then it could be used for next updates.
    - pros : minimal Downtime, easy rollback, testing in production like environment,
    - cons : Infrastructure costing 

- Canary Deployment:[IMP]
    - Defi : If there two version v1 and v2 and we want to deploy new version , so both are deployed and out of 10% of the initial traffic is transferred fromm v1 to v2 and if thhrere is no but the slowly the whole traffic is transferred.
    - pros : reduced risk, continuous feedback, user segmentation[user with certail type who uses that changed feature are transferrred on that server]
    - cons : complexity, gradual rollout time.

- Shadow Deployment:[maybe]
    - Defi : If there two version v1 and v2 and we want to deploy new version , so both are deployed with user request are being replicated to v2 whose responses are used as testing which only devs can see while user are getting response from v1 only.
    - pros : risks free testing, performance benchmarking
    - cons : Infrastructure overhead, no user feedback. 

- Ramped/Rolling/Updates Deployment:[IMP]
    - Defi : If there two version v1 and v2 and we want to deploy new version , so both are deployment and machines of v1 server are then slowly transferred to v2.
    - pros : No Downtime, resource efficiency[no two environment], good scalability,
    - cons : partial rollback complexity, deployment speed is slower. 

- A/B Testing Deployment:[maybe]
    - Defi : If there two version v1 and v2 and we want to deploy new version , so both are deployed and mobile user traffic is shifted and v2 and monitoring is done if result are good the whole traffic is moved. v1 and v2 could be completely different codebase. 
    - pros : Data driven decisions, user feedback
    - cons : complexity, user experience consistency 

