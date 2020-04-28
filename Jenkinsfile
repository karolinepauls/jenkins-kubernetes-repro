pipeline {
   parameters {
    string(name: 'STRING_PARAM_DEFAULT', defaultValue: '')
    string(name: 'STRING_PARAM_NO_DEFAULT')
  }

  agent {
    kubernetes {
      yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
    - name: c
      image: alpine
      args: [cat]
      tty: true
'''
    }
  }

  stages {
    stage('deploy') {

      steps {
        container('c') {
            sh 'echo 1'
        }
      }
    }
  }
}
