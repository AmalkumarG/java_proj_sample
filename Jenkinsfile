pipeline{
    agent {
        label "node1"
    }
    tools{
        maven "maven3"
    }
    parameters {
        string defaultValue: 'production', name: 'server'
    }
    environment {
        userpass = "set46%^$fhj"
    }
    stages{
        stage("build"){
            steps{
                echo "this is build block $params.server"
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