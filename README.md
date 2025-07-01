# java
Java installation:
If java isn’t installed, click on this link:https://www.oracle.com/java/technologies/downloads/
jdk21 WindowsMSIdouble click
Copy path with binsystem variablesdouble click pathadd java path
Check by Cmd : java --version
Jenkins installation:
Click https://www.jenkins.io/download/ downloadcopy path where it downloadednavigate to path in cmd
Write Java –jar Jenkins.war save password   http://127.0.0.1:8080  
Tomcat installation:
 https://tomcat.apache.org/   : latest version binary distribution32-bit window zip unzipdouble clickenter same username and password
Jenkins and Tomcat setup:
Copy the Jenkis.war file which was downloaded from the previoussection and copy it to the webapps folder in the tomcat folder.
Browse to cmd and navigate to tomcate folder and then bin run command startup.bat . 
It showed error like java home or jre not defined again go to environmental variables and create  a new variable in user variable named JAVA_HOME and give path of java jdk folder and again open cmd go to the tomcat folder and run the command 
http://127.0.0.1:8080/jenkins
Jenkins Git Setup:
Click manage Jenkinspluginsavailiable plugins serach Git Pushcheck ,install .
Restart , to check: new itemfreeproject/ ok sorce code management – git can be seen click git and fill details. if error install git and add path in Jenkins global tool configurations.
Jenkins home directory :
System variables new variable JENKINS_HOME , value = C:\Program Files restart by Java –jar Jenkins.war
Jenkins setup build jobs :
Github new repo
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins!");
    }
}
Now Jenkins dashboardnew item freestyle select github project insert repo pathbranch specifier */main  Now go to the Build section and click on Add build step → Execute Windows batch command In the command window, enter the following commands and then click on the Save button.
Javac HelloWorld.java
Java HelloWorld
Savebuild now
Jenkins pipelines:
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                // Here you can define commands for your build
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
                // Here you can define commands for your tests
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                // Here you can define commands for your deployment
            }
        }
    }
}
In githubnew item multibranch pipeline sources github add link .
Environment variable:
http://127.0.0.1:8080/env-vars.html/
Maven:
pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    environment {
        MBL_VERSION = '1.3.0'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building Project'
                echo "Building version ${env.MBL_VERSION}"
                bat 'mvn install'
            }
        }
    }
}
dash board -> Manage Jenkins -> Toolsmaven name should match.
Jenkins with parameter :
Take code from sara-saeed1 github in own github commit changes on jenkin it will show build with parameters uncheck execute test boxbuild.

