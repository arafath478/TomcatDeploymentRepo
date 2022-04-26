pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven_install"
    }

    stages {
        stage('SCM') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'stable', url: 'https://github.com/arafath478/TomcatDeploymentRepo.git'

            }
        
         }
       stage('Build') {
            steps {
                // To run Maven on a Windows agent, use
                 bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        
         }
         
       stage('Deploy') {
            steps {
               // Deploy to tomcat server
              deploy adapters: [tomcat9(credentialsId: 'Tomcatadmin', path: '', url: 'http://localhost:9090/')], contextPath: 'DevopsApplication', war: '**/*.war'       
                }
         }
     }
    post{
        success{
         echo "build success by yasar arafath shaik"
        }  
    }
}
