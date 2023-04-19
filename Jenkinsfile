pipeline {
    agent {label 'Deploy'}
    environment {
        USER_CREDENTIALS = credentials('HELLO')
        KEY = credentials('API_KEY')
    }
    stages {
        stage('IBM Script') {
            steps {                
                sh 'curl -fsSL https://clis.cloud.ibm.com/install/linux | sh'
                sh 'ibmcloud --version'
                sh 'ibmcloud config --check-version=false'
                sh 'ibmcloud plugin install cloud-object-storage'
            }
        }

        stage('Deploying Script') {
            steps {
                sh 'ibmcloud login --apikey "${KEY}" --no-region'
                sh 'ibmcloud cos object-put --bucket s2k-guestbook --key index.html --body index.html'  
            }
        }
    }
}

