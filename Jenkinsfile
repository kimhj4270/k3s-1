pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/kimhj4270/k3s.git', branch: 'master'
      }
    }
    stage('docaker build') {
      steps {
        sh '''
        '''
      }
    }

    stage('K8S Manifest Update') {
        steps {
            git url: 'https://github.com/best-branch/k8s-manifest.git', branch: 'master'
            sh "git add ."
            sh "git commit -m 'k3s-deployment'"
            sshagent(credentials: []) {
                sh "git remote set-url origin git@github.com:best-branch/k8s-manifest.git"
                sh "git push -u origin master"
             }
        }
        post {
                failure {
                  echo 'K8S Manifest Update failure !'
                }
                success {
                  echo 'K8S Manifest Update success !'
                }
        }
    }
  }
}
