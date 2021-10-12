pipeline{
    agent{
        label "master"
    }
    tools { 
        maven 'Maven 3.6.3' 
        jdk 'jdk 11'
    }
    stages{
        stage("building"){
            steps{
                sh "mvn clean package"
            }
        }
	stage("Testing") {
	    steps{
		sh "mvn clean test"
	    }
	}        
    }
    post{
       always{
            mail to: 'mohd.saifi@knoldus.com',
			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
        }            
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
