pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    
environment{
    PATH = "/opt/apache-maven-3.9.5/bin:$PATH"
}

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis'){
        environment{
           scannerHome = tool 'tito-sonar-scanner'
        }
        steps{
         withSonarQubeEnv('tito-sonarqube-server'){
            sh "${scannerHome}/bin/sonar-scanner"
        }
        }
     }
    }
}