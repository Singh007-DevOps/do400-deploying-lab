pipeline {

  agent {

    noede { label "maven" }

  }

  

  stages {

    stage ('test') {

      steps {

        sh "./mvnw verify"

        

      }

    }

  }

}


