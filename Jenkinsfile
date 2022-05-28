pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"
    }

    stages {
        stage('SCM - Checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'stable', url: 'https://github.com/arafath478/TomcatDeploymentRepo.git'

            }
        
         }
        
       stage('Build') {
            steps {
                // To run Maven on a Windows agent, use
             //    bat "mvn -Dmaven.test.failure.ignore=true clean package"
                sh 'mvn clean package'
            }
        
         }
         stage('Deploy') {
            steps {
               deploy adapters: [tomcat8(credentialsId: 'TomcatAdminUser', path: '', url: 'http://35.89.152.212:8090/')], contextPath: 'TomcatApplicationPipeline', war: '**/*.war'
            }
        
         }
         
      
     }
    post{
        always{
         echo "Job finished"
        }
        success{
         echo "Build success by yasar arafath"
        }
        failure{
         echo "Build failed by yasar arafath"
        }  
    }
}
