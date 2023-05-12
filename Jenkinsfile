pipeline{
    agent any
     stages{
         stage('Git Checkout'){
             steps{
                 git branch: 'main', credentialsId: 'github-credentials', url: 'https://github.com/dillibabu2077/hiring'
             }
         }
         stage('mvn clean package'){
             steps{
                sh 'mvn clean package' 
             }
         }
         stage('Deploy on Tomcat'){
             steps{
                sshagent(['tomcat-creds']) {
                       sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.91.14:/opt/tomcat9/webapps/"
                       sh "ssh ec2-user@172.31.91.14 /opt/tomcat9/bin/shutdown.sh"
                       sh "ssh ec2-user@172.31.91.14 /opt/tomcat9/bin/startup.sh"
}
             }
         }
     }
}
