pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/kimhj4270/k3s.git', branch: 'master'
      }
    }
    stage('cp manifest') {
      steps {
        sh 'sudo cp -r /root/k3s/ /root/cd/'
      }
    }

    stage('K8S Manifest Update') {
      steps {
        sh '''
          sudo git add /root/cd/k3s/*
          sudo git commit -m "Commit from Jenkins"
        '''            
        withCredentials([usernamePassword(credentialsId: 'jitoo', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'git push https://$username:$password@github.com/jitoo/k3s.git'
        }
      }
    }

  }
}
