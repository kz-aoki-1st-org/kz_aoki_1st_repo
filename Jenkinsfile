#!groovy

node {

	properties([
		pipelineTriggers([
			[
				$class: 'hudson.triggers.TimerTrigger',
				spec  : "0 0 * * 0"
			]
		])
	])

	stage("test") {
	
		echo "******** 1stJob test Start ********"

		sh "echo `date` >> job_date.txt"

		echo "******** On Jenkins Master ********"
		sh "ls -la "
		echo "******** On Jenkins Master ********"

		archive "job_date.txt"
		
		echo "******** 1stJob test End ********"

	}
}
