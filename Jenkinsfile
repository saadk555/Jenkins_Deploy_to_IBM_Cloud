pipeline {
    agent {label 'Deploy'}
    environment {
        USER_CREDENTIALS = credentials('HELLO')
        KEY = credentials('API_KEY')
    }
    stages {
        stage('IBM Script') {
            steps {
                sh 'sudo curl -fsSL https://clis.cloud.ibm.com/install/linux | sh'
                sh 'sudo ibmcloud --version'
                sh 'sudo ibmcloud config --check-version=false'
            }
        }

        stage('Deploying Script') {
            steps {
                sh 'sudo ibmcloud login --apikey "${KEY}"'
                sh 'sudo ibmcloud cos object-put --bucket s2k-guestbook --key index.html --body index.html'  
            }
        }
    }
}

