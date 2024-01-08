pipeline{
  agent{
    node{
      label 'maven-slave'
    }
  }


  stages{
  stage("Sample"){
  steps{
   touch npl.txt
  }
  }
  stage("Plane") {
  steps{
    touch ucl.txt
  }
  }
  }
}  


