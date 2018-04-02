pipeline {
  agent {
    node {
      label 'master'
    }
    
  }
  stages {
    stage('Exec_A') {
      steps {
        parallel(
          "Exec_A": {
            dir(path: 'C:\\Devaraj\\Test\\') {
              bat(script: 'a.vbs', returnStatus: true, returnStdout: true)
            }
            
            
          },
          "Exec_B": {
            dir(path: 'C:\\Devaraj\\Test\\') {
              bat(script: 'b.vbs', returnStatus: true, returnStdout: true)
            }
            
            
          }
        )
      }
    }
  }
}