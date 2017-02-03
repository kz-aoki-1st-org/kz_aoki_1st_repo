#!groovy

node {

	properties([
		pipelineTriggers([
			[
				$class: 'hudson.triggers.TimerTrigger',
				spec  : "H 0 * * 0"
			]
		]),
		[
			$class: 'ParametersDefinitionProperty', 
			parameterDefinitions: [
				[
					$class: 'BooleanParameterDefinition', 
					name: 'BUILD_LIBRARY_SKIP', 
					description: 'チェックオンにするとビルド後のドキュメントライブラリビルドを実行しません。', 
					defaultValue: false
				]
			]
		],
		parameters(
			[
				booleanParam(
					name: 'BUILD_LIBRARY_SKIP', 
					defaultValue: false
				)
			]
		)
	])

	echo "******** Start 1stJob ********"
	
	stage("Param") {
		echo currentBuild.result
		echo BUILD_LIBRARY_SKIP
	}

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
		
		if( BUILD_LIBRARY_SKIP == true ) {
			echo "SKIP! - Build kz_aoki_2nd_repo"
		} else {
			build job: "kz-aoki-1st-org/kz_aoki_2nd_repo/${env.BRANCH_NAME}", wait: false
		}
	}
	
	echo "******** End 1stJob ********"
	
}
