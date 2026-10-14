pipeline{
    agent {
        label 'node1'
    }
    tools {
        maven 'maven123'
    }
    options {
        skipDefaultCheckout(true)
    }
    stages {
        stage ('clone') {

            steps {
                checkout scm
                sh 'mvn clean package'
            }
        }
        stage ('deploy') {
                steps {
                echo "hello this is deploy stage"
                sh"sudo cp /home/ubuntu/jenkins/workspace/demo/target/java-tomcat-maven-example.war  /opt/tomcat/webapps"
                dir("sudo /opt/tomcat/webapps"){
                    sh"sudo jar -xvf java-tomcat-maven-example.war"
                    sh"sudo cp java-tomcat-maven-example/* /opt/tomcat/myapp_dir"
                }
            }
            
        }
    }
}