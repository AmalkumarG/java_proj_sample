pipeline{
    agent {
        label "node1"
    }
    tools {
        maven 'maven123'
    }
    stages {
        stage ('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('deploy') {
            echo "hello this is deploy stage"
        }
    }
}