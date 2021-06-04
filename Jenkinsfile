pipeline{

	agent any
	
	stages{
		stage("Build"){
			steps{
				script{
					try {
					sh 'chmod 0775 set-up.sh'
					sh './set-up.sh'
					echo 'Succeeded!'
					} catch (err) {
					echo "Failed: ${err}"
					} finally {
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