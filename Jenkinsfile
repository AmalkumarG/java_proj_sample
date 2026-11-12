pipeline{
    agent {
        label "node1"
    }
    stages{
        stage('test'){
            steps{
               echo "this is test" 
            }
        }
        stage('build'){
            steps{
                echo "this is build"
            }
        }
        stage('deploy'){
            steps{
                echo 'this is deploy'
            }
        }
    }
}