pipeline{
    agent {
        label 'node3'
    }
        
    stages{
        stage("QG CHECK") {
            steps {
                script {
                    withSonarQubeEnv('sonarscanner') {
                        sh 'mvn clean sonar:sonar'
                    }
                }
            }
        }
    }
}
