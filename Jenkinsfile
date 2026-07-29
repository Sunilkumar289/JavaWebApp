pipeline{
agent any
stages{
 stage('build')
 {
 steps{
 sh '''
 echo 'hello javaWebApp'
 mvn clean package
 '''
 }
 }
 stage('Docker build')
 {
   steps{
   sh '''
      echo "Building Docker image..."
      docker build -t myrepo/javawebapp:latest .
      '''
   }
 }
 
}
}