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
                withCredentials([usernamePassword(credentialsId: 'docker-hub-pass', passwordVariable: 'passWord', usernameVariable: 'userName')]) {
                  sh "docker login -u eghboyer -p Obiwankenob1%"
                }

                sh "docker push eghboyer/devopslab:0.1"
            }
        }
  
      stage('Docker Deploy'){
            steps{
                ansiblePlaybook credentialsId: '058be9b6-4cbf-44c6-bdc3-c162609ced85', installation: 'ansible', inventory: 'dev.inv', playbook: 'deploy-docker.yml'
            }
        }
    
        
        
    }
    
}
