pipeline {
	def app
    agent { docker { image 'python:3.5.1' } }
    stages {
	stage('CLone Repository'){
		checkout scm
	}
        stage('build') {
            steps {
                sh 'python --version'
            }
	stage('Push image'){
	docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials'){
		app.push("${env.BUILD_NUMBER}")
		app.push("latest")
		}
        }
    }
}
