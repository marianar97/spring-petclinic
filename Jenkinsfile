pipeline {
    agent any 
    
    tools{
        jdk 'jdk17'
        maven 'maven'
    }
    
     stages{
        
        stage("Git Checkout"){
            steps{
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/marianar97/spring-petclinic'
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
}