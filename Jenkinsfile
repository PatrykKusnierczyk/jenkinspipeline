pipeline {
    agent any
    
    stages {
        stage('Build') {
            
            steps {
                sh 'mvn clean package'
            }
            
            post {
                success {
                    echo 'No Archiving'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
            
        }
        
        stage('Deploy to Staging') {
            
            steps {
               build job: 'deploy-to-staging' 
            }
            
        }
    }
    
}
