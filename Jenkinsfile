pipeline {
    agent {
        label 'docker'
    }

    stages {
        stage('Build from a Dockerfile') {
            steps {
                scripts {
                    sh 'docker build -t kady/docker-react -f Dockerfile.dev .'
                }
            }
        }
        stage('Run the tests') {
            steps {
                scripts{
                    env.DOCKER_BUILDKIT=1
                    sh 'docker run -e CI=true kady/docker-react npm run test'
                }
            }
        } 
    }
}