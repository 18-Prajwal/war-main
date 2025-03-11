pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage('Maven Clean') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('Maven Validate') {
            steps {
                sh 'mvn validate'
            }
        }
        stage('Maven Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Maven Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Maven Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Store Artifact into Nexus') {
            steps {
                sh 'mvn -s settings.xml clean deploy'
            }
            post {
                success {
                    echo 'Artifact stored successfully in Nexus'
                }
                failure {
                    echo 'Failed to store artifact in Nexus'
                }
            }
        }
    }

    post {
        always {
            echo 'Always Executing'
        }
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed! Check logs for details.'
        }
    }
}
