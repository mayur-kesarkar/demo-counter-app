pipeline{
    agent any

    stages{
        
        stage('git pull'){

steps{
    git branch: 'main', url: 'https://github.com/mayur-kesarkar/demo-counter-app.git'
}
        }
    stage('unit teting'){
    steps{
        sh 'mvn test'
    }
    }

    stage('integration test'){

        steps{
            sh 'mvn verify -DskipUnitTests'

        }
    }
        stage('maven build'){

        steps {
            sh 'mvn clean install'
        }

    }

 stage('SAST'){

        step{
            script{

            withSonarQubeEnv(credentialsId: 'sonar-api-key') {
               sh 'mvn clean package sonar:sonar'
}
            }
        }

        
    }

stage('Qualtiy gate'){

        step{
            script{

        waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api-key3' {
          
}
            }
        }

        
    }

        
           } 
        }
    
