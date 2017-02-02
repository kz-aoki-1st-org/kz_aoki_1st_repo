#!groovy

node {

	properties([
		pipelineTriggers([
			[
				$class: 'hudson.triggers.TimerTrigger',
				spec  : "H 0 * * 0"
			]
		])
	])

	stage("1st Job") {
	
		echo "******** Start 1stJob ********"
		
		stage("Create 1st_job.txt") {
			sh "echo `date` >> 1st_job.txt"
		}

		stage("ls") {
			echo "******** On Jenkins Master ********"
			sh "pwd; ls -la "
			echo "******** On Jenkins Master ********"
		}

		stage("archive 1st_job.txt") {
			archive "1st_job.txt"
		}

		stage("Build kz_aoki_2nd_repo") {
			echo "Result SUCCESS !!!"
			build job: "kz-aoki-1st-org/kz_aoki_2nd_repo/${env.BRANCH_NAME}", wait: false
		}
		
		echo "******** End 1stJob ********"
		
	}
}
