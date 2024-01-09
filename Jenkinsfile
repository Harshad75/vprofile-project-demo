registry = "https://harshad99999.jfrog.io/"
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
    stage("Push the Artifact to Jfrog Artifactory") {
      steps {
        script {
          echo '<--------------- Jar Publish Started --------------->'
          def server = Artifactory.newServer url:registry+"/artifactory" ,  credentialsId:"jfrog-credentials"
          def properties = "buildid=${env.BUILD_ID},commitid=${GIT_COMMIT}";
          def uploadSpec = """{
            "files": [
              {
                "pattern": "target/(*)",
                "target": "harshad-maven-libs-release-local/{1}",
                "flat": "false",
                "props" : "${properties}",
                "exclusions" : ["*.xml","*.properties","*.gif","*.jpg","*.png","*.css"]
                            }
                         ]
                     }"""
          def buildInfo = server.upload(uploadSpec)
          buildInfo.env.collect()
          server.publishBuildInfo(buildInfo)
          echo '<--------------- Jar Publish Ended --------------->' 
        }
      }
    }
  }
}  


