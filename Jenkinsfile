pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/kimhj4270/k3s.git', branch: 'master'
      }
    }

    stage('K8S Manifest Update') {
      steps {
        sh 'git init'
        sh 'git add /root/k3s'
        sh 'git commit -m "v2"'
        withCredentials([usernamePassword(credentialsId: 'jitoo', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'git push https://$username:$password@github.com/jitoo/k3s.git'
        }
      }
    }

  }
}
