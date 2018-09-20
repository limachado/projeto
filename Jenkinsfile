node{
  stage('SCM Checkout'){    
    git 'https://github.com/dluisb/projeto.git'
  }
  estage('Compile Package'){
    def mvnHome = tool name: 'MAVEN', type: 'maven'
    sh "${mvnHome}/bin/mvn package"
  }
}
