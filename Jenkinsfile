pipeline {
  agent {
    kubernetes {
      label 'maven-kaniko-agent'   // matches the Pod Template label
    }
  }
  stages {
    stage('Build with Maven') {
      steps {
        container('maven') {
          sh 'mvn clean package'
        }
      }
    }
    stage('Docker Build & Push with Kaniko') {
      steps {
        container('kaniko') {
          sh '''
            /kaniko/executor \
              --dockerfile=$WORKSPACE/Dockerfile \
              --context=$WORKSPACE \
              --destination=<your-dockerhub-username>/javawebapp:latest
          '''
        }
      }
    }
  }
}
