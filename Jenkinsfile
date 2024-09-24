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
   //                  timeout(time: 1, unit: 'HOURS') {
		 //    	def qg = waitForQualityGate()
		 //        if (qg.status != 'OK') {
			// 	error "Pipeline aorted due to quality gate failure: ${qg.status}"
			// }
   //                  }
		    timeout(time: 1, unit: 'HOURS') {
			def quality_gate = waitForQualityGate()
			if (quality_gate.status != 'OK') {
				error "${quality_gate.status} in the Pipeline, Doesn't meet criteria"
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
