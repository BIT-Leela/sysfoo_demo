pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
               sh 'mvn clean package'
            }
        }
        stage('Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war', fingerprint: true
            }
        }
        stage('Deployment'){
            steps{
                deploy adapters: [tomcat9:(url:'http://localhost:8081/', credentialsId: 'admin')],
                    war:'target/*.war',
                    contextPath: 'app'
            }
        }
    }
}

