
node 
  {		  
          tool {
                  maven 'maven'
          }             
	  stage ('workspace clean') {
	  cleanWs()	  
	  }
	  stage('GitSCM')
	  {
		  git url: 'https://github.com/knagu/spring-petclinic.git'
	  }	  
    	  stage('Build Stage')
	  {	   
	   sh "mvn clean"
	   echo "Build Successful"
	  }	  
	  	 	 
  }
