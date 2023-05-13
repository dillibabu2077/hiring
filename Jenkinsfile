pipeline{
    agent any
     stages{
         stage('mvn clean package'){
             when {
                 branch 'develop'
             }
             steps{
                sh 'mvn clean package' 
             }
         }
         stage('Deploy on Tomcat'){
             when {
                 branch 'develop'
             }
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
