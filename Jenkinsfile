pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ("Clean up"){
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo"){
      steps {
        sh "git clone https://github.com/kaiselhabib/jenkinstp3.git"
      }
    }
    stage("Generate backend image") {
    steps {
        dir("jenkinstp3") {
            sh "mvn clean install"
            sh "docker build -t backend ."
        }
    }
}
stage("Run docker compose") {
    steps {
        dir("jenkinstp3") {
            sh "docker-compose up -d"
        }
    }
}
}
}
