pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/kimhj4270/k3s.git', branch: 'main'
      }
    }

    stage('K8S Manifest Update') {
      steps {
        git branch: 'main',
            credentialsId: 'jitoo',
            url: 'https://github.com/jitoo/k3s'
        sh 'touch 1.1 && echo "1" >> ./1.1'
	sh 'git init'
        sh 'git add .'
        sh 'git config --global user.email "jjs_0719@naver.com"'
        sh 'git config --global user.name "jitoo"'
        sh 'sudo git commit -m "v2"'
        withCredentials([usernamePassword(credentialsId: 'jitoo', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'git push https://$username:$password@github.com/jitoo/k3s.git'
        }
      }
    }

  }
}
