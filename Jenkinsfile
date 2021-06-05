pipeline{

	// agent {
    //     label : docker { image 'maven:3.6.3' }
    // }
agent any

environment{
	dockerHome = tool 'jenkins-docker'
	mavenHome =  tool 'jenkins-maven'
	PATH ="$dockerHome/bin:$mavenHome/bin:$PATH"
}

stages{
stage("Checkout"){
	steps{
		echo "check out code"
		}
}

stage("Compile"){
			steps{
				sh "mvn clean compile"
			}
		}

stage("Test"){
	steps{
		sh "mvn test "
	}
}

stage("Integration Test"){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify "
			}
		}

stage("Build"){
steps{
script{
	try {
	echo "mvn  version: "
	sh 'mvn --version'
	echo "docker version: " 
	sh 'docker --version'
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
			echo ":) "
		}
		success{
			echo " congratz, successfully executed!!"
		}
		failure{
			echo "========Build execution failed========"
		}
	}
}
}
}
