pipeline {

  agent {

    node { label "maven" }

  }

  

  stages {

    stage ('test') {

      steps {

        sh "./mvnw verify"

        

      }

    }

  }

}


