pipeline{
  agent {
    label {
      label 'slave1'
    }
  }
  stages{
    stage('version-control'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'master-slave-jenkins', url: 'https://github.com/etechteam3group5/distributed-build.git']]])
      }
    }
    stage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            echo 'action1'
          }
        }
        stage('sub-job2'){
          steps{
            echo 'action2'
          }
        }
        stage('sub-job3'){
            steps{
                echo 'action3'
            }
        }
      }
    }
    stage('codebuild'){
      agent {
        label {
          label 'slave2'
        }
      }
      steps{
        sh 'cat /etc/passwd'
      }
    }
    stage('codecomplte'){
      agent {
        label {
          label 'slave3'
        }
      }
      steps{
        sh 'cat /etc/passwd'
      }
    }
  }
}
