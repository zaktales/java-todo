pipeline {
    agent any

    tools {
        gradle 'Gradle-6'
    }

    parameters {
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    }

    environment {
        VERSION_NUMBER = '1.0'
    }

    stages {
        stage('Build parameters') {
            steps {
                echo "You chose ${params.CHOICE}"
            }
        }
        stage('Clone repository') {
            steps {
                echo 'Cloning repository'
                git 'https://github.com/brianmarete/java-todo.git'
            }
        }
        stage('Build ') {
            steps {
                echo "Build number ${BUILD_NUMBER}"
                // withGradle() {
                    sh 'gradle build'
                // }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the project'
                // withGradle() {
                    sh 'gradle test'
                // }
            }
        }
    }
    post {
        success {
            echo 'Build ran succcessfully'
        }
        
        failure {
            echo 'Build failed'
        }
    }
}
