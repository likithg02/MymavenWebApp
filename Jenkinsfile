pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/likithg02/MymavenWebApp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'  // Packages into WAR → target/MyMavenWebApp.war
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'  // Run unit tests
            }
        }
        stage('Deploy') {
            steps {
                // Deploy WAR to Tomcat webapps directory
                 sh 'ls -l target/*.war'  // Verify WAR file is packaged
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
