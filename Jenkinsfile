pipeline {
    agent any

    environment {
        // Define any environment variables
        APP_NAME = 'MyApp'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean install'  // Replace with your actual build command (e.g., mvn, npm)
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn clean test'  // Again, adjust for your tech stack
                sh 'pwd'
                sh 'ls -ltR'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: '${WORKSPACE}/target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying application...'
                // Add your deployment script here
                //sh './scripts/deploy.sh'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
