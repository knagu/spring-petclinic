node 
  {
	  def mvnHome = tool 'maven'
	  
	  stage ('workspace clean') {
	  cleanWs()	  
	  }
	  stage('GitSCM')
	  {
		  git url: 'https://github.com/knagu/spring-petclinic.git'
	  }	  
    	  stage('Build Stage')
	  {	   
	   sh "${mvnHome}/bin/mvn -B clean install package"
	   echo "Build Successful"
	  }
	  stage('Test'){		  
		  sh "${mvnHome}/bin/mvn -B test"
		  echo "Tests successful"
	  }
          stage('deploy') {
		  withCredentials( [usernamePassword( credentialsId: 'tomcat', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
		  sh "curl -u $USERNAME:$PASSWORD -T /var/lib/jenkins/workspace/Petclinic/target/spring-petclinic-1.5.1.jar 'http://localhost:8081/manager/text/deploy?path=/Petclinic&update=true'"
		  }
		  echo "Deploy successful"
	  }	
	  	 	 
  }
