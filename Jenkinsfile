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
                sh"cp /home/ubuntu/jenkins/workspace/demo/target/java-tomcat-maven-example.war  /opt/tomcat/webapps"
                dir("/opt/tomcat/webapps"){
                    sh"jar -xvf java-tomcat-maven-example.war"
                    sh"cp java-tomcat-maven-example/* /opt/tomcat/myapp_dir"
                }
            }
            
        }
    }
}