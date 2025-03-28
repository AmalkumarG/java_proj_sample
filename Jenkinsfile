pipeline{
    agent {
        label "node1"
    }
    tools{
        maven "maven3"
    }
    parameters {
        choice choices: ['production', 'development'], name: 'servers'
    }
    environment {
        userpass = "set46%^$fhj"
    }
    stages{
        stage("build"){
            steps{
                echo "this is build block $params.servers"
                sh "mvn clean package -DskipTests"
            }
            
        }

        stage("test"){
            steps{
                echo "this is test block $userpass"
            }
            
        }

        stage("deploy"){
            steps{
                echo "this is deploy block"
            }
            
        }
    }
}