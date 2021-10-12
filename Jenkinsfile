pipeline {
    agent {
        label 'master'
    }
    stages {
        stage("Production") {
            steps {
                //echo "Production branch"
                sh "mvn clean package"
            }
        }
        stage("Testing") {
	        steps{
                sh "mvn clean test"
            }
        }
        
    }
    post {
         success {
            echo "Packaging successful"
        }
        failure {
            echo "Packaging unsuccessful"
        }
    }
}
