pipeline{
    agent {
        label 'node3'
    }
    tools {
        maven 'mvndocker'
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
