pipeline {
   agent any
   environment {
      LOCK_RESOURCE = 'lock1'
   }
   options {
      timeout(time: 90, unit: 'MINUTES')
//      disableConcurrentBuilds()
   }
   stages {
      stage('Info') {
         steps {
          sh 'env'
         }
      }
       stage('Build') {
           steps {
               lock(${LOCK_RESOURCE}") {    // locking step
               echo 'sleeping 30'
               sleep(30)
               }
           }
      }

      stage('Lock Env') {
      options {
         lock('lock2') // locking entire stage
      }
      stages {
         stage('Deploy') {
            steps {
               echo 'Deploying..'
               sleep(30)
            }
          }

         stage('Ftest1') {
            options {
               retry(2)
            }
            steps {
               echo 'Testing F1...'
               sleep(30)
            }
          }

         stage('Ftest2') {
            options {
               retry(2)
            }
            steps {
               echo 'Testing F2...'
               sleep(5)
               //error('you fail')
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
