pipeline{
   agent{
    label 'node1' 
   } 
   stages{
 
    stage("build"){
        steps{
            echo "build stage"
            sh "mvn package"
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