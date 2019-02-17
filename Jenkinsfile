pipeline {
    any agent
    
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
    }
}
