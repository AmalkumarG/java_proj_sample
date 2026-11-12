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
            }
        }
        stage('deploy'){
            steps{
                echo 'this is deploy'
            }
        }
    }
}