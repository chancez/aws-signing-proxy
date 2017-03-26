#!/usr/bin/env groovy
node ('docker') {
    checkout scm
    docker.image('golang:1.8').inside {
        sh '''
        mkdir -p $GOPATH/src/github.com/coreos/aws-signing-proxy
        cp main.go $GOPATH/src/github.com/coreos/aws-signing-proxy
        go build \
            -o aws-signing-proxy \
            $GOPATH/src/github.com/coreos/aws-signing-proxy
        '''
    }
    def app = docker.build 'quay.io/coreos/aws-signing-proxy:latest'
    app.push 'latest'
}
