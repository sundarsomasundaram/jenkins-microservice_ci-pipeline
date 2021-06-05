pipeline{

	// agent {
    //     label : docker { image 'maven:3.6.3' }
    // }
agent any

	stages{
		stage("Build"){
			steps{
				script{
					try {
					// echo "mvn --version: " sh 'mvn --version'
					echo "$PATH"
					echo "Build Number - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "JOB_NAME - $env.JOB_NAME"
					echo "BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL - $env.BUILD_URL"
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
