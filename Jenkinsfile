node {
    checkout scm
	def job_config = readYaml(file: "jenkins_job_config.yaml")

	def folders = config.folders
	def folders_dsls = folders.collect { """
						folder('${it.folder-path}') {
							description('${it.description}')
						}
					"""}
	echo("$folders_dsls")
	def jobs = config.jobs
	def jobs_dsls = jobs.collect { """
						pipelineJob('${it.job_path}') {
    						definition {
        						cpsScm {
            						scm {
                						git('${it.jenkinsfile_git_repo}')
                						scriptPath('${it.jenkinsfile_path}')
            						}
        						}
    						}
						}
					"""}
	echo("$jobs_dsls")
}