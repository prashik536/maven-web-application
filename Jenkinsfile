pipeline {
    agent any
    environment {
        TOMCAT_PATH = '/root/apache/apache-tomcat-9.0.82'
        BACKUP_PATH = '/mnt/Backup_snapshot'
        REMOTE_SERVER = 'root@172.31.47.27'
        REMOTE_TOMCAT_PATH = '/mnt/apache-tomcat-9.0.82'
    }
    stages {
        stage('continuous download') {
            steps {
                git url: 'https://github.com/prashik536/maven-web-application.git'
            }
        }
        stage('continuous build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('continuous upload/backup') {
            steps {
                sh "cp /root/.jenkins/workspace/maven-web-application/target/maven-web-application.war $TOMCAT_PATH/webapps/"
                sh "cp /root/.jenkins/workspace/maven-web-application/target/maven-web-application.war $BACKUP_PATH/"
            }
        }
        stage('continuous Deliver on Webserver') {
            steps {
                script {
                    // Copy the WAR file to the remote server
                    sh "scp /root/.jenkins/workspace/maven-web-application/target/maven-web-application.war $REMOTE_SERVER:$REMOTE_TOMCAT_PATH/webapps/"
                    
                    // Restart Tomcat on the remote server (adjust the command as needed)
                    sh "ssh $REMOTE_SERVER '$REMOTE_TOMCAT_PATH/bin/shutdown.sh; $REMOTE_TOMCAT_PATH/bin/startup.sh'"
                }
            }
        }
    }
}
