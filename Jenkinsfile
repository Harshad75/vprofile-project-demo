pipeline{
  agent{
    node{
      label 'maven-slave'
    }
  }


  stages{
  stage("Build the source code"){
  steps{
   sh 'mvn clean install -Dmaven.test.skip=true'
  }
  }
  stage("Plane") {
  steps{
    sh 'touch npl.txt'
  }
  }
  }
}  


