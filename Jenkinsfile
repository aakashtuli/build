pipeline {
		agent none
		environment {
			NODE_VER = '8.1.0'
		}
		stages {
			stage('Beginning') { agent any
				environment {
					DEPLOY_VERSION = 'Stage'
				}
				steps {
					echo 'Hello World'
					sh 'echo $NODE_VER'
					echo "${env.DEPLOY_VERSION}"
				}
			}

			stage('Who Am I?') { agent any
				steps {
					environment {
						DEPLOY_VERSION = 'Prod'
						}
						echo "${env.DEPLOY_VERSION}"
						sh 'host -t TXT pgp.michaelholley.us | awk -F \'"\' \'{print $2}\''
				}
			}
		}
}
