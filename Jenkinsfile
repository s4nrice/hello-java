pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/s4nrice/hello-java.git'
                    // Компиляция Java-кода
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
                    // Архивирование скомпилированных файлов в артефакт сборки
                    archiveArtifacts artifacts: 'Test.jar', onlyIfSuccessful: true
                }
            }
        }
    }

    post {
        success {
            // Действия, выполняемые при успешном выполнении пайплайна
            echo 'Win'
        }

        failure {
            // Действия, выполняемые при неудачном выполнении пайплайна
            echo ':('
        }
    }
}
