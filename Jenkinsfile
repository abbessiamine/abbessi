
pipeline {
    agent any
    stages {
        stage('Pull') {
            steps {
                script{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']] ,
				userRmoteConfigs: [[
				credentialsId: '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',
				url:'https://github.com/abbessiamine/abbessi.git']]])
            }
        }
    }
	}
	}
