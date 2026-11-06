
def run(cmd) {
    if (isUnix()) {
        sh cmd
    } else {
        bat cmd
    }
}

pipeline {
    agent any

    environment {
        REGISTRY = 'jenkin.azurecr.io'  // YOUR login server
        IMAGE    = 'hello-az'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    run "docker build -t ${IMAGE}:${BUILD_NUMBER} ."
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    run "docker run --rm ${IMAGE}:${BUILD_NUMBER} nginx -t"
                }
            }
        }
    }
}
