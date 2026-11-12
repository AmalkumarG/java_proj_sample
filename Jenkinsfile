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
            }
        }
        stage('deploy'){
            steps{
                echo 'this is deploy'
            }
        }
    }
}