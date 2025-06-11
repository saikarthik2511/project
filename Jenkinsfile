pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/<your-username>/<your-repo>.git'
                sh 'ls -l ${WORKSPACE}' // confirm files exist
            }
        }

        stage('Clean Apache Folder') {
            steps {
                sh 'sudo rm -rf /var/www/html/*'
            }
        }

        stage('Copy Files') {
            steps {
                // adjust this path if your files are in a subfolder like /web or /dist
                sh 'sudo cp -r ${WORKSPACE}/* /var/www/html/'
                sh 'ls -l /var/www/html' // confirm deployment
            }
        }

        stage('Restart Apache') {
            steps {
                sh 'sudo systemctl restart httpd'
            }
        }
    }
}
