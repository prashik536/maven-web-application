
currentBuild.displayName = "simple-java-maven-app-#"+currentBuild.number
pipeline{
    agent any
    
    stages {
        stage('continuous download') {
            steps {
                git 'https://github.com/mohan0306/maven-web-application.git'
            }
               
        }
        stage('continuous build') {
            steps {
                sh 'mvn clean install'
            }
        }
            stage('continuous upload/backup') {
            steps {
                sh 'cp /root/.jenkins/workspace/maven-web-app-deploy/target/maven-web-application.war /root/apache/apache-tomcat-9.0.75/webapps'
                sh 'cp /root/.jenkins/workspace/maven-web-app-deploy/target/maven-web-application.war /mnt/Backup_snapshot'
            }
               
        }
        stage('continuous Deliver on Webserver') {
            steps {
                sh 'ssh -i ssh-webserver.txt root@172.31.94.211 '
            }
        } 
}
   
}
