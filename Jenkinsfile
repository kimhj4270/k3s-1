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
	sh 'git init'
        sh 'git add .'
        sh 'git commit -m "v2"'
        sh 'git push -u origin main'
        
      }
    }

  }
}
