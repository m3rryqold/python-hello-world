pipeline {
    def app
	stage('CLone Repository'){
		checkout scm
	}
	stage('Build image'){
	app = docker.build('m3rryqold/python-hello-world')
	}
	stage('Test image'){
	app.inside{
		sh 'echo "Tests passed"'
	}
	}
	stage('Push image'){
	docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials'){
		app.push("${env.BUILD_NUMBER}")
		app.push("latest")
		}
}
