pipeline {
    agent any
    tools {
        maven 'Maven - 3.9.0'
    }
    stages {
        stage ('Checkout') {
            steps {
                git url: 'https://github.com/yaksh0210/multi_branch_jen.git', branch: env.GIT_BRANCH
            }
        }
        stage ('Build') {
            steps {
                script {
                    sh 'mvn clean package'
                }
            }
        }
        stage ('Test') {
            steps {
                script {
                    echo "Building Feature Branch -> ${env.GIT_BRANCH}"  
                    sh "java src/main/java/com/example/App.java"                  
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline Finished'
        }
        success {
            echo 'Status : Successfull'
        }
        failure {
            echo 'Status : Failed'
        }
    }
}
 