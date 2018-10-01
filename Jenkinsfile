pipeline {
   agent any
    stages {
       stage('Sonar') {
            steps {
                sh 'mvn sonar:sonar'
                sh 'echo verificado pelo sonar'
            }
        }
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
            try{
               sh 'docker rm -f maquinateste'
               sh 'docker run -d --name maquinateste -p 90:8080 projetolua'
            }catch(exc){
               sh 'docker run -d --name maquinateste -p 90:8080 projetolua'
            }
         }
        }
        stage ('subindo para o dockerhub') {
            steps {
                withCredentials([string(credentialsId: 'user', variable: 'USER'), string(credentialsId: 'pass', variable: 'PASS')]) {
                   sh 'docker tag projetolua luaivo14/projetolua'
                   sh 'docker login -u $USER -p $PASS'
                   sh 'docker push luaivo14/projetolua'
                   sh 'echo subiu para o dockerhub'
                }
            }
        }
     }
}
