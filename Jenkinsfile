pipeline {
	agent any
	  stages {
	    stage('Build App'){
	     steps {
	      bat 'mvn -f pom.xml clean package'
	      }
	      post {
	           success {
		   echo "Now archiving the artifacts"
		   archiveArtifacts artifacts '**/*.war'
		   }
	      }
	  }

	  stage ('Create tomcat Docker Image') {
	  	steps {
		  bat "echo current directory: && cd"
		  bat "dir"
		  bat "docker build . -t tomcatsamplewebapp_Solo:${env.BUILD_ID}"
		}
	}
	}
	}
