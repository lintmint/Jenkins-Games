pipeline {
   agent any
   options {
      timeout(time: 90, unit: 'MINUTES')
//      disableConcurrentBuilds()
   }
   stages {
       stage('Build') {
           steps {
               lock('lock1') {    // locking a step, not stage
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
