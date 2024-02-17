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

        steps{
            script{

           withSonarQubeEnv(credentialsId: 'sonar-api-key01') {
               sh 'mvn clean package sonar:sonar'
}
            }
        }

        
    }

stage('Qualtiy gate'){

        steps{
            script{

        waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api-key01' 
          

            }
        }

        
    }

        stage('nexus artificateupload'){

            steps{
                script{
                    nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Uber.jar', type: 'jar']], credentialsId: 'admin', groupId: 'com.example', nexusUrl: '13.127.139.49:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'demo-app', version: '1.0.0'
            }
        }
        
           } 
        }
    
