node {
	jobDsl scriptText: '''pipelineJob(\'createdFromSeedsJob\') {
	    definition {
	        cps {
	            script(\'\'\'node {
	   echo \'Hello World\'
	}\'\'\')
	            sandbox()
	        }
	    }
	}'''
}