pipeline {
  agent any
  options { skipDefaultCheckout(true) }

  stages {
    stage('Stage 1: Build') {
      steps {
        echo 'Task: Compile and package the application.'
        echo 'Example tool: Maven (or Gradle / npm).'
      }
    }
    stage('Stage 2: Unit & Integration Tests') {
      steps {
        echo 'Task: Run unit tests and basic integration tests.'
        echo 'Example tools: JUnit (Java) / Jest or Mocha (Node).'
      }
    }
    stage('Stage 3: Code Analysis') {
      steps {
        echo 'Task: Static code analysis to meet standards.'
        echo 'Example tools: SonarQube/SonarCloud, ESLint.'
      }
    }
    stage('Stage 4: Security Scan') {
      steps {
        echo 'Task: Scan code/dependencies for vulnerabilities.'
        echo 'Example tools: Snyk, OWASP Dependency-Check, npm audit.'
      }
    }
    stage('Stage 5: Deploy to Staging') {
      steps {
        echo 'Task: Deploy the app to a staging server (production-like).'
        echo 'Example: Docker image to AWS EC2 instance.'
      }
    }
    stage('Stage 6: Integration Tests on Staging') {
      steps {
        echo 'Task: Run integration/E2E tests against staging.'
        echo 'Example tools: Postman/Newman, Cypress, or same test runner.'
      }
    }
    stage('Stage 7: Deploy to Production') {
      steps {
        echo 'Task: Promote the tested build to production.'
        echo 'Example: Docker/Kubernetes or deploy to AWS EC2.'
      }
    }
  }
}
