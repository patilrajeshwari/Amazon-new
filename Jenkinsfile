pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the feature branch
                git branch: 'feature1', url: 'https://github.com/patilrajeshwari/Amazon-new.git'
            }
        }

        stage('Build and Test') {
            steps {
                // Build the project
                sh 'mvn clean install'
                
                // Run tests
                sh 'mvn test'
            }
        }

        stage('Merge to Main') {
            steps {
                // Check if tests passed
                script {
                    def testsPassed = sh script: 'mvn test', returnStatus: true
                    if (testsPassed == 0) {
                        // Checkout main branch
                        sh 'git checkout master'
                        
                        // Merge feature branch into main
                        sh 'git merge feature1'
                        
                        // Push changes to origin
                        sh 'git push origin master'
                    } else {
                        error('Tests failed on the feature branch, merge aborted.')
                    }
                }
            }
        }
    }
}

  
