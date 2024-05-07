pipeline {
	agent any 
	
	parameters {
                  choice choices: ['DEV', 'QA', 'UAT'], name: 'ENV'
                 }
	triggers {
  		pollSCM '* * * * *'
	}
	
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/piyush/Extracted/Maven_setup/apache-maven-3.9.6/bin/mvn install'

	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( env.ENV == 'DEV' ){
        	sh 'cp target/PIPELINE.war /home/piyush/Extracted/apache-tomcat-9.0.88/webapps'
        	echo "deployment has been COMPLETED on QA!"
			 }
			else if ( env.ENV == 'UAT' ){
    		sh 'cp target/PIPELINE.war /home/piyush/Extracted/apache-tomcat-9.0.88/webapps'
    		echo "deployment has been done on UAT!"
			}
			}}}	
}}
