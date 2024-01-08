pipeline{
  agent{
    node{
      label 'maven-slave'
    }
  }

environment {
  PATH = "/opt/apache-maven-3.9.6/bin:$PATH"

  stages{
  stage("Build the source code"){
  steps{
   sh 'mvn clean deploy -Dmaven.test.skip=true'
  }
  }
  stage("Plane") {
  steps{
    sh 'touch npl.txt'
  }
  }
  }
}  


