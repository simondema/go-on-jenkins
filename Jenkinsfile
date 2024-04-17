pipeline {
    agent any
    environment {
        GO111MODULES = 'on'
    }
    tools {
        go 'go-1.22.2'
    }
    stages {
        stage('Build') {
            steps {
                sh 'go build'
            }
        }
    }
}