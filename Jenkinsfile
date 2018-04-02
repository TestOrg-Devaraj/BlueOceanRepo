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
    stage('GitDownload') {
      steps {
        dir(path: 'C:\\Devaraj\\Test\\Git_Download\\') {
          git(url: 'https://github.com/TestOrg-Devaraj/StoreVBS_ToRunfromBlueOcean.git', branch: 'master', credentialsId: 'devarajranganathan')
        }
        
      }
    }
    stage('ExecuteGitContents') {
      steps {
        parallel(
          "ExecuteGitContents": {
            dir(path: 'C:\\Devaraj\\Test\\Git_Download\\') {
              waitUntil() {
                fileExists 'c.vbs'
              }
              
              bat(script: 'c.vbs', returnStatus: true, returnStdout: true)
            }
            
            
          },
          "Exec_D": {
            dir(path: 'C:\\Devaraj\\Test\\') {
              bat(script: 'd.vbs', returnStatus: true, returnStdout: true)
            }
            
            
          }
        )
      }
    }
    stage('CloseConfirmation') {
      steps {
        input(message: 'Can the Pipeline execution be closed', ok: 'Yes')
      }
    }
  }
}