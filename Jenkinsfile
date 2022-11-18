pipeline{
    agent any
    tools {
      maven 'MVH_HOME'
    }
    environment {
      DOCKER_TAG = getVersion()
    }
    stages{
        stage('mvn build') {
            steps {
                sh 'mvn -v'
        }
        
        stage('SCM'){
            steps{
                git credentialsId: 'github', 
                    url: 'https://github.com/Ricounobiwan/MAVEN_WAR_HELLO_WORLD.git'
            }
        }
        
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
        
#        stage('Docker Build'){
#            steps{
#                sh "docker build . -t eghboyer@gmail.com/hariapp:${DOCKER_TAG} "
#            }
#        }
#        
#        stage('DockerHub Push'){
#            steps{
#                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
#                    sh "docker login -u eghboyer@gmail.com -p ${dockerHubPwd}"
#                }
#                
#                sh "docker push eghboyer@gmail.com/hariapp:${DOCKER_TAG} "
#            }
#        }
#        
#        stage('Docker Deploy'){
#            steps{
#              ansiblePlaybook credentialsId: 'dev-server', disableHostKeyChecking: true, extras: "-e DOCKER_TAG=${DOCKER_TAG}", installation: 'ansible', inventory: 'dev.inv', playbook: 'deploy-docker.yml'
#            }
#        }
    }
}

def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}
