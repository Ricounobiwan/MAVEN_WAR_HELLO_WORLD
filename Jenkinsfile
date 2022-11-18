pipeline{
    agent any
    tools {
      maven 'MVN_HOME'
    }

    stages{
       stage('mvn build') {
         steps {
           sh 'mvn -v'
         }
       }
     
      stage('Maven Build'){
        steps{
          sh "mvn clean package"
        }
      }
       
      stage('Docker Build'){
            steps{
                sh "docker build . -t eghboyer/devopslab:0.1"
            }
        }
        
      stage('DockerHub Push'){
            steps{
                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
                    sh "docker login -u eghboyer -p Obiwankenob1%"
                }
                
                sh "docker push eghboyer/devopslab:0.1"
            }
        }
  

    }
}
