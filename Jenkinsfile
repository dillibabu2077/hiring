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
         stage('Tomcat Deploy-Dev'){
             when {
                 branch 'develop'
             }
             steps{
                echo "Deploy to Dev"
             }
         }
         stage('Tomcat Deploy-Prod'){
             when {
                 branch 'main'
             }
             steps{
                echo "Deploy to Production"
             }
         }
     }
}
