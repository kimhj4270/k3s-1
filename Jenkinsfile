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
        sh 'touch 1.1 && echo "2" >> ./1.1'
	sh 'git init'
        sh 'git add -u .'
        sh 'git config --global user.email "jjs_0719@naver.com"'
        sh 'git config --global user.name "jitoo"'
        sh 'sudo git commit -a -m "Update for Jenkins"'
        withCredentials([usernamePassword(credentialsId: 'jitoo', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'git remote set-url origin https://$username:$password@github.com/jitoo/k3s.git'
          sh 'git push origin +main --force'
        }
      }
    }

  }
}
