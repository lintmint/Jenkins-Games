pipeline {
   agent any
//   options {
//      disableConcurrentBuilds()
//   }
   stages {
       stage('Build') {
           steps {
               lock('lock1') {
               echo 'sleeping 30'
               sleep(30)
               }
           }
      }

      stage('Lock Env') {
      options {
         lock('lock2') 
      }
      stages {
         stage('Deploy') {
            steps {
               echo 'Deploying..'
               sleep(30)
            }
          }

         stage('Ftest1') {
            steps {
               echo 'Testing F1...'
               sleep(30)
            }
          }

         stage('Ftest2') {
            steps {
               echo 'Testing F2...'
               sleep(30)
            }
         }
      }
    }  // stage('Lock Env')

    stage('Unlocked stage') {
       steps {
          echo 'Nothing locked this stage....'
          sleep(30)
       }
     }
  }
}
