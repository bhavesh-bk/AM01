pipeline{
	agent any
	environment{
		LANG='en_US.UTF-8'
		LCALL='en_US.UTF-8'
	}
	tools{
		maven 'Maven'
	}
	stages{
		stage('Checkout'){
			steps{
				git branch:'master' , url:'https://github.com/bhavesh-bk/AM01.git'
				}
			}
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('Archive'){
			steps{
				archiveArtifacts artifacts:'target/*.war' , fingerprint:true
				}
			}
		stage('Deploy'){
			steps{
				sh 'mvn clean package'
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
				}
			}
		}
	}
