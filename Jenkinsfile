pipeline {
    agent any
    environment {
        GOOGLE_APPLICATION_CREDENTIALS = credentials('f7345d20-d2b8-4f91-8d0b-7b78a8e37a73')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Check out the source code from your version control system (e.g., Git)
                    git 'https://github.com/djsurani/simeple_html_css_page.git'
                    
                    // Use Google Cloud Storage plugin with the configured credentials
                    sh "gcloud auth activate-service-account --key-file=${GOOGLE_APPLICATION_CREDENTIALS}"
                    
                    // Ensure the script is executable and execute the deployment script
                    sh "chmod +x deploy.sh"
                    sh "./deploy.sh"
                }
            }
        }
    }
}
