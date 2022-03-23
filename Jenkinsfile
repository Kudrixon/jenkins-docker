pipeline {
    agent {
        node {
            label 'TestNode'
        }
    }
    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Choose your brach name - default is set to master')
    }
    stages {
        stage('git') {
            steps {
                git credentialsId: '1',
                url: 'https://github.com/Kudrixon/jenkins-docker.git',
                branch: "${params.BRANCH}"
            }
        }
        stage('whatever2') {
            steps {
                sh 'docker system prune -af'
                sh 'docker build -t codi:latest .'
                sh 'docker stop codiwebtest || true && docker rm -f codiwebtest || true'
                sh 'docker run -d -p 8888:8888 --name codiwebtest codi'
            }
        }
    }
}
