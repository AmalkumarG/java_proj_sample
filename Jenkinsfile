pipeline{
    agent {
        label "node1"
    }
    options{
        skipDefaultCheckout(true)
    }
    tools{
        maven 'maven123'
    }
    stages{
        stage('build'){
            steps{
                checkout scm
                echo "this is build"
                sh'mvn clean package'
                sh 'mkdir -p extract'
                sh 'cp /home/ubuntu/jenkins/workspace/demo/target/java-tomcat-maven-example.war /home/ubuntu/jenkins/workspace/demo/extract'
                sh '''
                    cd /home/ubuntu/jenkins/workspace/demo/extract
                    jar -xvf java-tomcat-maven-example.war
                '''
                sh "rm -rf /home/ubuntu/jenkins/workspace/demo/extract/java-tomcat-maven-example.war"
                sh 'cp -r /home/ubuntu/jenkins/workspace/demo/extract/* /opt/tomcat/myapp_dir/'
                sh 'systemctl restart tomcat.service'

            
            }
        }
        stage('deploy'){
            steps{
                echo 'this is deploy'
            }
        }
    }
}