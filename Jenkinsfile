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
}
}