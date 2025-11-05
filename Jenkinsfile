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
            sh "mkdir -p unstash"
            dir('unstash'){
                unstash 'build'
            }
        }
    }
    stage('deploy'){
        agent{
            label 'node1'
        }
        steps{
        dir('unstash/target'){
            sh "jar -xvf *.war"
        }
        }

    }
    
   }
}
