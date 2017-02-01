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
	
		echo "******** 1stJob test Start ********"

		sh "echo `date` >> 1st_job.txt"

		echo "******** On Jenkins Master ********"
		sh "pwd; ls -la "
		echo "******** On Jenkins Master ********"

		archive "1st_job.txt"
		
		if (currentBuild.result.equals("SUCCESS")) {
			echo "Result SUCCESS !!!"
			build job: "kz-aoki-1st-org/kz_aoki_2nd_repo/${env.BRANCH_NAME}", propagate: false, wait: false
		}
		
		echo "******** 1stJob test End ********"
		
	}
}
