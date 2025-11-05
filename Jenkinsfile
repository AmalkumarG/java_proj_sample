pipeline{

agent none

    options {
    skipDefaultCheckout true
    }

   stages{
 
    stage("build"){
        agent{
            label 'node1'
        }
        steps{
            echo "build stage"
            checkout scm
            sh "mvn package"
            stash name: 'build', includes: 'target/*.war'
        }
    }
    stage("test"){
        agent{
            label 'node2'
        }
        steps{
            echo "test stage"
            unstash 'build'
        }
    }
    stage("deploy"){
        steps{
            echo "deploy stage"
        }
    }
   }
}
