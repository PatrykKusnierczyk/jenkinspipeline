pipeline {
    any agent
    
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
                vat "docker build . -tag tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
}
