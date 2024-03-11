pipeline {
    agent any
    
	 tools {
        maven 'maven'
    }
	
    
    stages {
		stage('Checkout') {
            steps {
                checkout scm
            }
        }
		
        stage('Generate Artifact') {
            steps {
                echo 'Generating artifact...'
                bat 'mvn clean package'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        
        stage('Generate Report') {
            steps {
                echo 'Report Generation'
                bat 'mvn jacoco:prepare-agent test jacoco:report'
            }
        }
    }
}
