pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                // Checkout the repo that contains index.html
                git 'https://github.com/saikarthik2511/project.git'
            }
        }

        stage('Deploy HTML') {
            steps {
                // Clean up default Apache file and deploy your index.html
                sh '''
                sudo rm -f /var/www/html/index.html
                sudo cp index.html /var/www/html/index.html
                '''
            }
        }

        stage('Restart Apache') {
            steps {
                sh 'sudo systemctl restart httpd'
            }
        }
    }
}
