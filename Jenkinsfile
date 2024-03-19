pipeline {
	agent any
	stages {
		stage('Checkout') {
            steps {
                // Checkout the feature branch
                git  'https://github.com/patilrajeshwari/Amazon-new.git'
            }
        }

		stage ('build') {
			steps {
				sh 'mvn clean install'
			}
		
		}
		stage ('test') {
			steps {
				sh 'mvn test'
			}
	
	}
}
}
