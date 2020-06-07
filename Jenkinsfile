pipeline {
  agent any
  stages {
    stage('Build Application') { 
      steps {
        bat 'mvn clean install'
      }
    }
 	stage('Test') { 
      steps {
        echo 'Test Appplication...' 
        bat 'mvn test'
      }
    }
 	
    stage('Deploy CloudHub') { 
    	      environment {
        ANYPOINT_CREDENTIALS = credentials('wp.anypoint.credentials')
      }
       steps {
        echo 'Deploying only because of code commit...'
        echo " deploying to  ${params.env} environent"
         echo " worker is  ${params.workerType}"
        bat 'mvn package deploy -DmuleDeploy -Dusername="exceed007-4" -Dpassword=Teju@123 -Denvironment=SANDBOX -DworkerType=Micro -Dworkers=1 -Dregion=us-east-1'
      }
    } 
  }
}