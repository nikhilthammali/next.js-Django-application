pipeline {
    agent any

    stages {
        stage('Test') {
            steps {

                sh 'cd frontend && npm install && npm test'
                sh 'cd backend  && pip install -r dependencies.txt
                sh 'python manage.py collectstatic --noinput'
            }
        }
        stage('Build') {
            steps {

                sh 'docker build -t your-backend-image backend/'
                sh 'docker build -t your-frontend-image frontend/'
            }
        }
        stage('Deploy') {
            steps {

                sh 'docker run -d -p 8000:8000 your-backend-image'
                sh 'docker run -d -p 3000:3000 your-frontend-image'
            }
        }
    }
}
