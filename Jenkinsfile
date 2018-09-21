pipeline {
   agent any
    stages {
       stage('Build') {
            steps {
                sh 'mvn clean package'
                sh 'echo clean package realizado'
            }
        }
        stage('build') {
            steps {
                sh 'docker build --tag projetolua .'
                sh 'echo build realizado'
            }
        }
        stage ('subindo para o dockerhub') {
            steps {
                sh 'echo subindo para o dockerhub'
                sh 'docker tag projetolua luaivo14/projetolua'
                sh 'docker login -u $DOCKER_USER -p $DOCKER_PASSWORD'
                sh 'docker push luaivo14/projetolua'
            }
        }
     }
}
