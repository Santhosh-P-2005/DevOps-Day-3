pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/Santhosh-P-2005/DevOps-Day-3.git'
            }
        }
        stage('Build') {
            steps{
                sh 'mvn clean'
		sh 'mvn install'
            }
        }
        stage('build to images') {
            steps {
            script{
                sh "docker build -t santhosh9405/webapplication1 ."
            }
            }
        }
        stage('docker push hub') {
            steps {
            script{
               withDockerRegistry(credentialsId: 'cred-3', url: 'https://index.docker.io/v1/') {
                sh 'docker push santhosh9405/webapplication1'
            }
            }
            }
        }
    }
}
