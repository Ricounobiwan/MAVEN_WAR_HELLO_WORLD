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
        

    }
}
