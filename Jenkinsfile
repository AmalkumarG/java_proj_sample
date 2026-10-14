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
                sh"mkdir -p extracted"
                sh"cp target/java-tomcat-maven-example.war extracted"
                sh"""
                    cd extracted
                    jar -xvf java-tomcat-maven-example.war
                    rm -rf extracted/java-tomcat-maven-example.war
                """
                sh"sudo cp -r extracted/*  /opt/tomcat/myapp_dir"

            }
            
        }
    }
}