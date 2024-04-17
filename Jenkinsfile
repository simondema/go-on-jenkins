pipeline {
    agent any
    environment {
        GO111MODULES = 'on'
    }
    tools {
        go 'go-1.12'
    }
    stages {
        stage('Build') {
            steps {
                sh 'go build'
            }
        }
    }
}