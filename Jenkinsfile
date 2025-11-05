pipeline{

agent none

    options {
    skipDefaultCheckout true
    }

   stages{
 
    stage("build"){
        agent{
            label 'node2'
        }
        steps{
            echo "build stage"
            checkout scm
            sh "mvn package"
            stash name: 'build', includes: 'target/*.war'
        }
    }
    stage('unstash'){
        agent{
            label 'node1'
        }
        steps{
            sh "mkdir unstash"
            dir('unstash'){
                unstash 'build'
            }
        }
    }
    stage('deploy'){
        dir('unstash/target'){
            sh "java -xvf *.war"
        }
    }
    
   }
}
