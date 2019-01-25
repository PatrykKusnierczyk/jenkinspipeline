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
        
        stage('Deploy to Production') {
            steps {
                timeout(time:5, UNIT: 'DAYS') {
                    input message: 'Approve production deployment?'
                }
                
                build job: 'deploy-to-prod'
            }
            
            post {
                success {
                    echo ' Code deployed to Production'
                }
                
                failure {
                    echo 'Deployment Failed!'
                }
            }
        }
    }
    
}
