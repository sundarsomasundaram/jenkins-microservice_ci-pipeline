pipeline{

	agent { any }


	stages{
		stage("Build"){
			steps{
				script{
					try {
					echo "mvn --version: " sh 'mvn --version'
					sh 'chmod 0775 set-up.sh'
					sh './set-up.sh'
					} catch (err) {
					echo "Failed: ${err}"
					} finally {
					sh 'chmod 0775 tear-down.sh'
					sh './tear-down.sh'
					}
					echo 'Printed whether above succeeded or failed.'
				}
			}
			post{
				always{
					echo "========inside Build always========"
				}
				success{
					echo "========Build executed successfully========"
				}
				failure{
					echo "========Build execution failed========"
				}
			}
		}
	}
}