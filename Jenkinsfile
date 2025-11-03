pipeline{
   agent{
    label 'node1' 
   } 
   stages{
    stage("git clone"){
        steps{
            echo "git clone stage"
        }
    }
    stage("build"){
        steps{
            echo "build stage"
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