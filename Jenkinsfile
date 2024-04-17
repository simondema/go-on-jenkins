pipeline {
    agent any
    environment {
        GO111MODULES = 'on'
        CODECOV_TOKEN = 'e85b7cd8-f595-421e-9789-3f8e97baf6f4'
    }
    tools {
        go 'go-1.12'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building.'
                sh 'go build'
            }
        }
        stage('Test') {
            steps {
                sh 'go test ./... -coverprofile=coverage.txt'
                sh 'curl -s https://codecov.io/bash | bash -s -'
            }
        }
        stage('Code Analysis') {
            steps {
                sh 'curl -sfL https://install.goreleaser.com/github.com/golangci/golangci-lint.sh | bash -s -- -b $GOPATH/bin v1.18.0'
                sh 'golangci-lint run'
            }
        }
        stage('Release') {
            when {
                buildingTag()
            }
            environment {
                GITHUB_TOKEN = credentials('GITHUB_TOKEN')
            }
            steps {
                sh 'curl -sL https://git.io/goreleaser | bash'
            }
        }
    }
}