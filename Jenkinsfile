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
		stage('Build') {
		     steps {
			    script{
				sh"ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
				}
				}
				}
				
      stage('docker')
        {
             steps {
                    script{
             sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml -e 'ansible_python_interpreter=/usr/bin/python3' "
                          }
                   }
          } 
      
      stage('push to dockerhub')
        {
             steps {
                    script{
             sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml --ask-become-pass"
                          }
                   }         
        } 
        
    
	}
	}
