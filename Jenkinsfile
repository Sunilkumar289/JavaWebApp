pipeline {
  agent any
  tools {
    maven 'Maven-3.9.16'
  }
  stages {
    stage('Build with Maven') {
      steps {
        container('maven') {
          sh 'mvn clean package'
        }
      }
    }
    stage('Docker Build & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                        docker build -t $DOCKER_USER/javawebapp:latest .
                        docker push $DOCKER_USER/javawebapp:latest
                    '''
                }
      }
    }
  }

