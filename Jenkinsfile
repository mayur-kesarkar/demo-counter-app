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


            
           } 
        }
    
