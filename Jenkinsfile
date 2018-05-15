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
				environment {
					DEPLOY_VERSION = 'Prod'
				}
				steps {
						echo "${env.DEPLOY_VERSION}"
						sh 'host -t TXT pgp.michaelholley.us | awk -F \'"\' \'{print $2}\''
				}
			}

		stage('Deploy to stage?') { agent none
			steps {
					input 'Deploy to stage?'
				}
			}
			stage('Parallel') { agent any
				failFast true
				parallel {
					stage('Build 1') {
						steps {
							echo "It's ME!""
						}
					}

					stage('Build 2') {
						steps {
							echo 'Not it's me!'
						}
					}
				}
			}
		}
}
