pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Code cloned successfully!'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo pm2 stop myapp || true
                    sudo pm2 start app.js --name myapp
                    sudo pm2 save
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployed successfully!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
