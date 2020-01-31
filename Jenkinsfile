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
	   sh "${mvnHome}/bin/mvn -B clean verify package"
	   echo "Build Successful"
	  }
	  stage('Test'){		  
		  sh "${mvnHome}/bin/mvn -B test"
		  echo "Tests successful"
	  }
	  	 	 
  }
