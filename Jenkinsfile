pipeline{
    agent any
    tools {
      maven 'MVH_HOME'
    }

    stages{
        stage('mvn build') {
            steps {
                sh 'mvn -v'
        }
        
        stage('SCM'){
            steps{
                git credentialsId: 'github', 
                    url: 'https://github.com/Ricounobiwan/MAVEN_WAR_HELLO_WORLD'
            }
        }
        
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
        
/*        stage('Docker Build'){
#            steps{
#                sh "docker build . -t eghboyer/spring-hello-world:0.1 "
#            }
#        }
#        
#        stage('DockerHub Push'){
#            steps{
#                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
#                    sh "docker login -u eghboyer@gmail.com -p ${dockerHubPwd}"
#                }
#                
#                sh "docker push eghboyer/spring-hello-world:${DOCKER_TAG} "
#            }
#        }
#        
#        stage('Docker Deploy'){
#            steps{
#              ansiblePlaybook credentialsId: 'dev-server', disableHostKeyChecking: true, extras: "-e DOCKER_TAG=${DOCKER_TAG}", installation: 'ansible', inventory: 'dev.inv', playbook: 'deploy-docker.yml'
#            }
#        }
*/
    }
}
