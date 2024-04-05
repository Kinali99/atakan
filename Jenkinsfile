pipeline {
    agent any
    stages {
        stage('Build test hamid') {
            steps {
                script {
                    // Navigera till TrailrunnerProject-mappen
                    dir('TrailrunnerProject') {
                        sh 'mvn compile'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Navigera till TrailrunnerProject-mappen
                    dir('TrailrunnerProject') {
                        sh 'mvn test'
                    }
                }
            }
        }
        stage('Post Test') {
            steps {
                script {
                    // Navigera till TrailrunnerProject-mappen
                    dir('TrailrunnerProject') {
                        // Kör junit-kommandot för att läsa in testrapporter
                        junit '**/TEST*.xml'
                    }
                }
            }
        }
        stage('Build and Test Python Project') {
            steps {
                script {
                    bat 'python -m robot C:/Users/kinal/.jenkins/workspace/Labb Jenkins/Selenium'
                }
            }
            post {
                always {
                    robot outputPath: 'C:/Users/kinal/.jenkins/workspace/Labb Jenkins', passThreshold: 80.0, unstableThreshold: 70.0, onlyCritical: false
                }
            }
        }
    }
}
