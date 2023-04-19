pipeline {
    agent {label 'Deploy'}
    environment {
        USER = credentials('HELLO')
    }
    stages {
        stage('Run Script') {
            steps {
                sh 'echo "successful"'
                sh 'echo $USER'
                
            }
        }
    }
}
