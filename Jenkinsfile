pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        
        stage('Test SIT') {
            when {
                branch 'SIT'
            }
            steps {
                echo 'Running SIT tests...'
                // Add your SIT test steps here
            }
        }
        
        stage('Test QA') {
            when {
                branch 'QA'
            }
            steps {
                echo 'Running QA tests...'
                // Add your QA test steps here
            }
        }
        
        stage('Test UAT') {
            when {
                branch 'UAT'
            }
            steps {
                echo 'Running UAT tests...'
                // Add your UAT test steps here
            }
        }
        
        stage('Deploy to Production') {
            when {
                branch 'master' // or the branch you use for production
            }
            steps {
                script {
                    def userInput = input(
                        id: 'userInput', message: 'Approve Production Deployment?', parameters: [
                        [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Approve deployment?', name: 'approve']
                    ])
                    
                    if (userInput['approve']) {
                        echo 'Deploying to Production...'
                        // Add your production deployment steps here
                    } else {
                        error 'Deployment to Production was not approved.'
                    }
                }
            }
        }
    }
}
