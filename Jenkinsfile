pipeline {
    
    agent any
    
    stages{
        
        stage('checkout clone'){
            steps{
                git branch: 'feature/2026.02.10', credentialsId: 'vickky9494', url: 'https://github.com/vickky9494/Petclinic.git'
            }
        }
        stage('Build'){
            steps{
                bat 'mvn install'
            }
        }
        stage('Test'){
           steps{
               
           }
        }
		stage(Generated Test Reports){
		steps{ 
		        junit 'target/*surefire-reports/*.xml'
		   }
	    }
       
        stage('Gererated the Artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
         stage('Deploy'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'TomCatCredentials', path: '', url: 'http://localhost:8080/')], contextPath: 'TomCat pipeline Application', war: 'target/*.war'
            }
        }
}
}
