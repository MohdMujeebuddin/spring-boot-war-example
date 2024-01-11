pipeline{
    agent any
    tools {
        maven 'maven' 
    }
    stages{
        stage("test"){
            steps{
                // mvn test
                sh 'mvn test'
                echo "========executing A========"
            }
            
        }
        stage("build"){
            steps{
                sh "mvn package"
                echo "========executing A========"
            }
            
        }
        stage("deploy to test"){
            steps{
                // deploy to container
                deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://54.83.135.160:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
            
        }
        stage("deploy to prod"){
            steps{
                // deploy to container
                deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://54.145.230.86:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
            
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
