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
       stage('subir container') {
         steps {
             sh 'docker run -d --name maquinateste -p 90:8080 projetolua'
         }
        }
        stage ('subindo para o dockerhub') {
            steps {
                sh 'docker tag projetolua'
                sh 'docker login -u luaivo14 -p #rfembr64'
                sh 'docker push luaivo14/projetolua'
               sh 'echo subiu para o dockerhub'
            }
        }
     }
}
