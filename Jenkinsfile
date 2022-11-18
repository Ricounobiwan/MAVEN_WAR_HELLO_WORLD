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
        

    }
}
