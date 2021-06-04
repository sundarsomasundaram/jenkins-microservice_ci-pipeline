pipeline{

	agent any
	
	stages{
		stage("Build"){
			steps{
				script{
					sh './set-up.sh'
					try {
					sh 'might fail'
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