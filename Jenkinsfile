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
        sh 'sudo git remote set-url origin https://jitoo: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@github.com/jitoo/k3s.git'
        sh 'sudo git push -u origin --all'
      }
    }

  }
}
