def environments = [

  'dev',

  'qa',

  'uat',

  'prod'

]
 
pipeline {
 
  agent any
 
  stages {
 
    stage('Deploy') {

      steps {

        script {

          for (env in environments) {

           echo "Loop success"

          }

        }
    }
}



