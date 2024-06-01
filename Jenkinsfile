pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }

	
    
    stages {
        stage('SCM Checkout') {
            steps {
        
                git branch: 'main' , url: 'https://github.com/Devolu-shiva/banking-project.git'
		
            }
		}
        stage('Maven Build') {
            steps {
                
                sh "mvn package"
            }
		}

	         stage('html publisher') {
            steps {
                
               publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/bankitt/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
            }
		}

	      stage('Create a Docker image from the Package bankingapp.jar file restart docker and jenkins') {
      steps {
       echo 'this step to create a docker image of our running application in our remode docker '
        sh 'docker build -t devshivadevops96/bankhub:1.0 .'
                    }
            }

	 

    }
}
