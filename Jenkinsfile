pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/s4nrice/hello-java.git'
                    sh 'javac -d . Test.java'
                    sh 'jar cvfm Test.jar manifest.txt Test.class'
                    sh 'ls'
                    sh 'java -jar Test.jar'
                    sh 'ls'
                }
            }
        }

        stage('Archive') {
            steps {
                script {
                    archiveArtifacts artifacts: 'Test.jar', onlyIfSuccessful: true
                }
            }
        }
    }

    post {
        success {
            echo 'Win'
        }

        failure {
            echo ':('
        }
    }
}
