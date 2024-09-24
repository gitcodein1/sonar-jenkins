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
                    timeout(time: 1, unit: 'HOURS') {
		    	def quality_gate = waitForQualityGate()
		        if (quality_gate.status != 'OK') {
				error "Pipeline Failed due to quality gate failure: ${qg.status}"
			}
                    }
                }
            }
        }
        // stage("BUILD") {
        //     steps {
        //         sh 'mvn package'
        //     }
        // }
    }
}
