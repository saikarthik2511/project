pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/saikarthik2511/project.git'
            }
        }

        stage('Build') {
            steps {
                echo "No build required for static HTML app"
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                sudo rm -rf $DEPLOY_DIR/*
                sudo cp -r * $DEPLOY_DIR/
                sudo systemctl restart httpd
                '''
            }
        }
    }

    post {
        success {
            echo "Deployment Successful"
        }
        failure {
            echo "Deployment Failed"
        }
    }
}

