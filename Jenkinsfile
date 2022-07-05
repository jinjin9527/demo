pipeline {
    agent any

    stages {
        stage('pull') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '980d9f39-2d5e-4c81-9ee6-85c8b931b307', url: 'git@github.com:jinjin9527/demo.git']]])
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('deploy'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '71de3841-bed8-4a05-9c34-c2891b9b29a8', path: '', url: 'http://192.168.1.15:8080/')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
