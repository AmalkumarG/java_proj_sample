pipeline{
agent{
    label "node1"
}

   tools{
    maven "maven123"
   }
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
            // sh "mvn package"
        }
    }
    stage("test"){
        steps{
            echo "test stage"
        }
    }
    stage("deploy"){
        steps{
            echo "deploy stage"
        }
    }
   }
}