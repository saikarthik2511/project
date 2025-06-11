pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/saikarthik2511/project.git'
            }
        }

        stage('Clean Apache Directory') {
            steps {
                sh "sudo rm -rf ${DEPLOY_DIR}/*"
            }
        }

        stage('Deploy Files to Apache') {
            steps {
                sh "sudo cp -r * ${DEPLOY_DIR}/"
            }
        }

        stage('Restart Apache') {
            steps {
                sh "sudo systemctl restart httpd"
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
