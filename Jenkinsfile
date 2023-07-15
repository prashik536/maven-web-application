
currentBuild.displayName = "simple-java-maven-app-#"+currentBuild.number
pipeline{
    agent any
    
    stages {
        stage('continuous download') {
            steps {
                git 'https://github.com/mohan0306/simple-java-maven-app.git'
            }
               
        }
        stage('continuous build') {
            steps {
                sh 'mvn clean install'
            }
        }
//             stage('continuous upload') {
//             steps {
//                 sh 'cp /root/.jenkins/workspace/Jenkinsfile/target/my-app-1.0-SNAPSHOT.jar /root/apache/apache-tomcat-9.0.75/webapps'
//                 sh 'cp /root/.jenkins/workspace/Jenkinsfile/target/my-app-1.0-SNAPSHOT.jar /mnt/Backup_snapshot'
// //              sh 'scp /root/.jenkins/workspace/Game_Of_life/gameoflife-web/target/gameoflife.war ansible@172.31.86.205:/mnt'
//             }
               
//         }
}
   
}
