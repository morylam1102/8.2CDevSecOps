pipeline {
  agent any
  options {
    skipDefaultCheckout(true)
    timestamps()
  }
  environment {
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Install & Build') {
      steps {
        sh '''
          if [ -f package-lock.json ]; then npm ci; else npm install; fi
          npm run build || true
        '''
      }
    }

    stage('Unit Tests') {
      steps {
        sh 'npm test -- --ci --reporters=jest-junit || true'
      }
      post {
        always {
          junit allowEmptyResults: true, testResults: '**/junit*.xml, **/jest-junit*.xml'
        }
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''
          if [ -f .eslintrc* ]; then npm run lint || npx eslint . || true; fi
        '''
      }
    }

    stage('Package Artifact') {
      steps {
        sh 'tar czf build-artifacts.tgz * || true'
        archiveArtifacts artifacts: 'build-artifacts.tgz', fingerprint: true, onlyIfSuccessful: false
      }
    }

  }

  post {
    always {
      cleanWs()
    }
  }
}

