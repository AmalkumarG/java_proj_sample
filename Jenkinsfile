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