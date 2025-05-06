pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/vikeshkumar8210/Ubuntu_Policies.git'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: "${REPO_URL}"
            }
        }

        stage('Apply Security Policies') {
            steps {
                script {
                    // Ensure the script is executable and run it with sudo
                    sh 'chmod +x apply_policies.sh'
                    sh 'sudo ./apply_policies.sh'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Security policies applied successfully.'
        }
        failure {
            echo '❌ Failed to apply policies. Check the logs for more details.'
        }
    }
}
