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
        sh '''
          sudo cp -r /root/k3s/* /root/cd/k3s
        '''
      }
    }

    stage('K8S Manifest Update') {
      steps {
        sh '''
          cd /root/cd/k3s
          git add .
          git commit -m "Commit from Jenkins"
        '''            
        withCredentials([usernamePassword(credentialsId: 'jitoo', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'git push https://$username:$password@github.com/jitoo/k3s.git'
        }
      }
    }

  }
}
