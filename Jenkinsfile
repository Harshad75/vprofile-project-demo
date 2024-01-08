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
  stage("Unit test") {
  steps{
    sh 'mvn surefire-report:report'
  }
  }
  }
}  


