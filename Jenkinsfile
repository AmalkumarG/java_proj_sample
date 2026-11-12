pipeline{
    agent {
        label "node1"
    }
    options{
        skipDefaultCheckout(true)
    }
    stages{
        stage('build'){
            steps{
                checkout scm
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