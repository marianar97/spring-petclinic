pipeline {
    agent any

    environment {
        DOCKER_NETWORK = 'dev_network' 
        DOCKER_IMAGE = 'sandboxSpringPetClinic'
        DOCKERFILE_PATH = 'sandbox_dockerfile'
        def mvnHome = tool name: 'maven397', type: 'hudson.tasks.Maven$MavenInstallation'
    }

    stages{
        
        stage("Git Checkout"){
            steps{
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/rajeshmamuddu/Petclinic-project.git'
            }
        }
        
        stage("Compile"){
            steps{
                sh "mvn clean compile"
            }
        }
        
         stage("Test Cases"){
            steps{
                sh "mvn test"
            }
        }
    }

    post {
        success {
            echo 'Build successful.'
        }
        failure {
            echo 'Build Failure.'
        }
    }
}