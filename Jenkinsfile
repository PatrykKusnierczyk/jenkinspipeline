pipeline {
    any agent
    
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
                vat "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
    }
}
