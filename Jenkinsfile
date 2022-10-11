pipeline{
  agent any
stages {
  stage('download') {
    steps 
    {
        git branch: 'feature', url: 'https://github.com/lavoisierbleriot/deployment_test.git'
    }
  }

  stage('build') {
    steps {
      sh 'mvn package'
    }
  }
  
   stage('deploy') {
    steps {
      deploy adapters: [tomcat8(credentialsId: 'cool', path: '', url: 'http://172.31.26.138:8080')], contextPath: 'qaenv', war: '**/*.war'
    }
  }

  stage('testing') {
    steps {
      echo 'testing has failed'
    }
  }

  stage('release') {
    steps {
        input 'waiting for authorization'
      deploy adapters: [tomcat8(credentialsId: 'cool2', path: '', url: 'http://172.31.20.90:8080')], contextPath: 'prodenv', war: '**/*.war'
    }
  }

}

    
 }
