pipeline {

    agent {label 'Slave-3'}

    tools {
        maven "maven"
        jdk "jenkins-jdk"
    }

    triggers {
        pollSCM "* * * * *"
    }
    
    stages
    {
        stage("Cleanup")
        {
            steps
            {
                sh 'mvn clean'
            }
        }
        
        stage("Test")
        {
            steps
            {
                sh 'mvn test'
                echo "hello"
            }
        }
        stage("Package")
        {
            steps
            {
                sh 'mvn package'
                echo 'sucess'
            }
        }
    }

post{
        always{
            mail to: 'mohd.saifi@knoldus.com',
			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
        }
}
