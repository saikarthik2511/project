pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/saikarthik2511/project.git'
                sh 'ls -l' // debug
            }
        }

        stage('Clean Target') {
            steps {
                sh "sudo rm -rf ${DEPLOY_DIR}/*"
            }
        }

        stage('Copy Files') {
            steps {
                sh "sudo cp -r ${WORKSPACE}/* ${DEPLOY_DIR}/"
                sh "ls -l ${DEPLOY_DIR}" // verify deployment
            }
        }

        stage('Restart Apache') {
            steps {
                sh 'sudo systemctl restart httpd'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful.'
        }
        failure {
            echo '❌ Deployment failed.'
        }
    }
}
