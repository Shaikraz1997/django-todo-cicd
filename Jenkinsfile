pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Shaikraz1997/Django.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t django-app .'
            }
        }

        stage('Run Migrations') {
            steps {
                sh "docker run --rm django-app python manage.py migrate"
            }
        }

        stage('Run App') {
            steps {
                sh "docker run -d -p 8000:8000 django-app"
            }
        }
    }
}
