pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello From GitHub hook trigger'
            }
        }
        stage('build') {
            steps {
                echo 'build'
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html s3://jenkins-sugawara/')
                }
            }
        }
        stage('test') {
            steps {
                echo 'test'
            }
        }
        stage('release') {
            steps {
                echo 'release'
            }
        }
    }
}
