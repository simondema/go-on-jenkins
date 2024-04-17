pipeline {
    agent any
    environment {
        GO111MODULES = 'on'
    }
    tools {
        go 'go'
    }
    stages {
        stage('Build') {
            echo 'Building...'
            sh 'go build'
        }
    }
}