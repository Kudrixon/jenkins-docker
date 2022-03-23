pipeline {
    agent any
    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Choose your brach name - default is set to master')
    }
    stages {
        stage('git') {
            steps {
                credentialsId: '1',
                url: 'https://github.com/Kudrixon/jenkins-docker.git',
                branch: "${BRANCH}"
            }
        }
        stage('whatever2') {
            steps {
                sh 'imageName=codi:${BUILD_NAME}'
                sh 'containerName=Codiwebtest' 
                sh 'docker system prune -af'
                sh 'docker stop $containerName || true && docker rm -f $containerName || true'
                sh 'docker run -d -p 8888:8888 --name $containerName $imageName'
            }
        }
    }
}
