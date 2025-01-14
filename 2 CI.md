# Continuous Integration

- Parts of CI:
    1. Continuous integrate the code in Git repository
    2. Integration will occur multiple time based on config.
    3. Early error detection,faster release cycle and reduce integration problem.

# Git 

- in CLI = git clone <https method> = to clone remote repo
- In vscode open terminal by default it is a powershell in vscode change it to git bash
    - ls -a = to see if .git folder is created that means it is cloned.
    - cd .git = to go into the folder to see .git files

    - .. = is address to previous directory eg ls .. = show previous directory
    - ./ = is address to current directory eg ls ./ = show current directory
    - git branch -a = to show all branch
    - clone [git] = clone to local
    - fork [github] = to take from other account

- Other way is to clone is to do = git init and then create a repo in the git and do the commands that are in that repo page.
    - git init
    - git branch -M main
    - git remote add origin <https-methods> = origin is alias to https
    - Incase if already exist then below two more steps
        [
        - git fetch [branch] ::
            - fetch doesnot do pull
            - brings all the new changes in the repository [branch/branch-name-change]
        - git pull [code+branch] ::
            - pull also does fetch
            - pull + fetch = brings all the new changes in the repository [code/branch/branch-name-change]
        ]
    - git push -u origin main = -u for first time

echo "Hello.. This is my first jenkins Demo: %date%:%time%"
1.46

# Jenkins
- Initial admin passwords path = C:\ProgramData\Jenkins\.jenkins\secrets
- Initial admin password now = 65d40be6396442ffab55c9f858ba078c

- create new project [freestyle]
- add any description
- add new build 
    - choose window batch command for windows user
    - choose shell command for linux user
    - paste = echo "Hello.. This is my first jenkins Demo: %date%:%time%"
    - O/P = "Hello.. This is my first jenkins Demo: 06-10-2024: 2:56:48.36"
    - Run build >> build schedule >> go to console output.
    - Plugin = will be able to use nodejs commands.
- save

# Jenkins Pipeline

- set of multiple steps used to get the desired result.
- It is a concept of multiple commands where the first command output is the input for the next commands.
    eg In CMD = ls | tail -1 [here "|" is used to separate two commands]

- steps:
0. Code come from Github
1. Compile the code, build the application, install the dependency
2. 


- 1. create new item
    2. select pipeline
    3. Go to pipeline defination >> select pipeline script with scm > choose SCM as git > enter repo link >> Add jenkins >> 
    in KIND select username with password[do with ssh also] > give username and password as github username/password>>id can be any [git]>>
    select the credential 
    4. select branch as main not master // it is git branch which we are selection 
    5. script path as Jenkinsfile

    6. open the git code in vs 
    - no need to run the server.
    7. create app.test.js file and copy the below code in the square braces.
    7.1 install = npm install jest supertest --save-dev
    8. change test to jest in package.json file = "scripts": {
    "test": "jest"}
    9. Now in cli run = npm test
    [ 
        // app.test.js
    import { request } from "supertest";
    import { app } from "./app.js";

    describe("GET /", () => {
        it("should return Welcome to App", async () => {
            const res = await request(app).get('/');
            expect(res.statusCode).toBe(200);
            expect(res.text).toEqual("Welcome to App");
        });
    });
    // Use toEqual for String Comparison: While toBe works for string comparison in this context, toEqual is more semantically appropriate for checking the equality of two strings.
    ]

    10. create a filename "Jenkinsfile" and it is called as groovy script with no extension, with below data: in sq-braces
        [    
        pipeline{
            agent any

            stages{
                stage('install Dependencies'){
                    steps{
                        bat 'npm install'
                    }
                }
                stage('Run Tests'){
                    steps{
                        bat 'npm test'
                    }
                }
            }
        }
        ]

11. push alll in the git
12. go to the pipeline and build it and click on #num >>> console output.

- now this will install all the dependency of our app and run the test cases in the jenkins.

- here we have done unit testing and in integration test [click a button see the response all is done in test case only]


# Triger jenkins job via github::
- on github
    - go to repo >> setting >> webhooks >> add webhook >> add payload url eg"url+/github-webhook/" [only work for remote instance for eg [ec2]and not for localhost:8080] >> ssl-certification [disable-for-test-purpose] >> check the active and save it.
- on jenkins:
    - go to configure >> build-the trigger [check 3rd option] "Github hook triger ..." and done.

    s
# try by own [continuous-feedback]
    - mail to in groovy script

# Note:
- echo is a print statement in linux and powershell