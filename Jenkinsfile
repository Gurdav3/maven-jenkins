pipeline {
  agent any // means run on any machine that is available to Jenkins
  tools {
        maven "M3" 
   }

  stages {
      stage('Build Artifact') 
      {
            steps 
            {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }  
       }
      stage('Test Maven - JUnit') 
      {
            steps 
            {
              //sh "mvn test"
              echo "Running unit tests"
            }
      }
      stage('Dev Environment') 
      { 
          steps 
          { 
              echo 'Deploying to Production Environment' 
          } 
      }
    stage('Test Environment') 
      { 
          steps 
          { 
              echo 'Deploying to Test Environment' 
          } 
      }
    stage('UAT Environment') 
      { 
          steps 
          { 
              input('Do you want to continue?')
              echo 'Deploying to UAT Environment' 
          } 
      }
    stage('Production Environment') 
      { 
          steps 
          { 
              input('Do you want to continue?')
              echo 'Deploying to Production Environment' 
          } 
      }
    }
}
