pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        string defaultValue: 'hello_all', name: 'value'
    }
    stages{
        stage('build'){
            steps{
                echo "this is $params.value"
                sh "mvn clean package"
            }
        }
        stage('test'){
            steps{
                echo 'this is test'
            }
        }
        stage("stashing"){
            steps{
                dir('target/'){
                    stash name:"war_file",includes:"*.war"
                }
            }
        }

        stage("unstash"){
            agent{
                label "node2"
            }
            steps{
                sh "mkdir stashed;cd stashed"
                unstash "war_file"
            }
        }
        // stage('test2'){

        //     steps{

        //         echo 'this is test'
        //         sh "mkdir dir1"
        //         sh "touch file2"
        //     }
        // }
        stage('deploy'){
            steps{
                echo 'this is deploy'
                sh "docker stop tomcat && docker rm tomcat"
                sh "docker run -d --name tomcat -p 80:8080 tomcat"
                sh "docker cp target/*.war tomcat:/usr/local/tomcat/webapps"
            }
        }
    }
}

