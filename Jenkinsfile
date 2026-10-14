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
            }
            
        }
    }
}