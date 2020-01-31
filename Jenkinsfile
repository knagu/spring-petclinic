/*
pipeline {
    agent none 
    stages {
        stage ('Checkout') {
          steps {
            git 'https://github.com/knagu/spring-petclinic.git'
          }
        }
        stage('Build') {
            //agent { docker 'maven:3.5-alpine' }
            steps {               
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        //stage('Deploy') {
          //steps {
            //input 'Do you approve the deployment?'
            //sh 'scp target/*.jar jenkins@192.168.50.10:/opt/pet/'
            //sh "ssh jenkins@192.168.50.10 'nohup java -jar /opt/pet/spring-petclinic-1.5.1.jar &'"
          //}
        //}
    }
}
*/
node 
  {
	  
	  
	  stage ('workspace clean') {
	  cleanWs()	  
	  }
	  stage('GitSCM')
	  {
		  git url: 'https://github.com/knagu/spring-petclinic.git'
	  }	  
    	  stage('Build Stage')
	  {	   
	   sh "mvn -B clean verify package"
	   echo "Build Successful"
	  }
	  stage('Test'){		  
		  sh "${mvnHome}/bin/mvn -B test"
		  echo "Tests successful"
	  }
	  stage('deploy') {
		  withCredentials( [usernamePassword( credentialsId: 'tomcat', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
		  sh "curl -u $USERNAME:$PASSWORD -T /var/lib/jenkins/workspace/ApplicationDemo@2/gameoflife-web/target/gameoflife.war 'http://localhost:8081/manager/text/deploy?path=/GameofLife&update=true'"
		  }
		  echo "Deploy successful"
	  }	 	 
  }
