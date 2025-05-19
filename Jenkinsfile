// pipeline{
//     agent{
//         label 'node1'
//     }
//     tools{
//         maven 'maven123'
//     }
//     parameters {
//         string defaultValue: 'hello_all', name: 'value'
//     }
//     stages{
//         stage('build'){
//             steps{
//                 echo "this is $params.value"
//                 sh "mvn clean package"
//             }
//         }
//         stage('test'){
//             steps{
//                 echo 'this is test'
//             }
//         }
//         stage('test2'){
//             agent {
//                 label "node2"
//             }
//             steps{

//                 echo 'this is test'
//                 sh "mkdir dir1"
//                 sh "touch file2"
//             }
//         }
//         stage('deploy'){
//             steps{
//                 echo 'this is deploy'
//                 sh "docker stop tomcat && docker rm tomcat"
//                 sh "docker run -d --name tomcat -p 80:8080 tomcat"
//                 sh "docker cp target/*.war tomcat:/usr/local/tomcat/webapps"
//             }
//         }
//     }
// }


pipeline {
    agent {
        label 'node1'
    }

    tools {
        maven 'maven123'
    }

    options {
        skipDefaultCheckout(true) // Disable automatic checkout on all agents
    }

    parameters {
        string(name: 'value', defaultValue: 'hello_all')
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm // Explicit SCM checkout only on node1
            }
        }

        stage('Build') {
            steps {
                echo "This is ${params.value}"
                sh "mvn clean package"
                // Stash build artifacts to share with node2 if needed
                stash includes: 'target/*.war', name: 'appArtifact'
            }
        }

        stage('Test') {
            steps {
                echo 'This is test'
            }
        }

        stage('Test2') {
            agent {
                label 'node2'
            }
            steps {
                echo 'This is test2 on node2, no git clone here'
                unstash 'appArtifact' // Retrieve artifact from node1
                sh "mkdir dir1"
                sh "touch file2"
            }
        }

        stage('Deploy') {
            steps {
                echo 'This is deploy'
                sh "docker stop tomcat || true && docker rm tomcat || true"
                sh "docker run -d --name tomcat -p 80:8080 tomcat"
                sh "docker cp target/*.war tomcat:/usr/local/tomcat/webapps"
            }
        }
    }
}
