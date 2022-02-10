pipeline{
    agent any
    stages{
       // stage('Cloning repo'){
         //   steps{
           //     sh "git clone https://github.com/Mohit722/SampleWebApplication.git"
            //}
        //}
     stage('Build'){
            tools{
               maven 'M2'
            }
            steps{
                dir('SampleWebApplication'){
                    sh "mvn clean package"
                }
            }
       stage('unit test'){
        steps{
            junit 'SampleWebApplication/TestCalculator_JUnitResult.xml'
        }
        }
        stage('Deploy to tomcat') {
            steps {
            dir('sparkjava-war-example'){
               deploy adapters: [tomcat9(credentialsId: 'tomcat' , path: '', url: 'http://ec2-15-207-115-111.ap-south-1.compute.amazonaws.com:8080')], contextPath: null, war: 'target/sparkjava-hello-world-1.0.war'
        }
    }
    }
}}
