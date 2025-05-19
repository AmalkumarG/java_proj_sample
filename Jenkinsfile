pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        choice choices: ['prod', 'dev'], name: 'servers'
    }
    options{
        skipDefaultCheckout(true)
    }
    stages{
        stage('build'){
            steps{
                checkout scm
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
                sh "rm -rf stashed;mkdir stashed;cd stashed"
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
            when{
                    expression{params.servers=="dev"}
                }
            agent{
                    label "node1"
                }
            steps{

                
                echo 'this is deploy'
                sh "docker stop tomcat && docker rm tomcat"
                sh "docker run -d --name tomcat -p 80:8080 tomcat"
                sh "docker cp target/*.war tomcat:/usr/local/tomcat/webapps"
            }
        }
    }
}

