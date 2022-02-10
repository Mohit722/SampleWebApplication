pipeline{
    agent any
    stages {
    
        stage('Pulling Code form repo') {
            steps {
		url: 'https://github.com/Mohit722/SampleWebApplication.git'
                 
                
               }
            }
        
              stage('Build'){
                steps{
                    dir ('SampleWebApplication'){
                        sh "./mvnw package"
                    }
                }
            } 
	  stage ('Test'){
		  steps{
			  dir('SampleWebApplication'){
				  sh './mvnw test'
			  }
		  }
		  post {
			  always{
				 junit 'SampleWebApplication/TestCalculator_JUnitResult.xml'

			  }
		  }
	  }
        stage('Deploy to tomcat') {
            steps {
            dir('sparkjava-war-example'){
               deploy adapters: [tomcat9(credentialsId: 'tomcat' , path: '', url: 'http://ec2-15-207-115-111.ap-south-1.compute.amazonaws.com:8080')], contextPath: null, war: 'target/sparkjava-hello-world-1.0.war'
        }
    }
    }
}
    }
