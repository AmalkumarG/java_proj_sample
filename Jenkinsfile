pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    stages{
        stage('build'){
            steps{
                echo "this is build"
                sh "mvn clean package"
                
            }
        }
        stage('test'){
            steps{
                echo 'this is test'
            }
        }
        stage('deploy'){
            steps{
                echo 'this is deploy'
            }
        }
    }
}