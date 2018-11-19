node {
    checkout scm
	def config = readYaml(file: "jenkins_job_config.yaml")

	def folders = config.folders
	def folders_dsls = folders.collect { """
						folder('${it.folder_path}') {
							description('${it.description}')
						}
					"""}

	def jobs = config.jobs
	def jobs_dsls = jobs.collect { """
						pipelineJob('${it.job_path}') {
						    triggers {
                                githubPush()
                            }
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

	def final_dsl = folders_dsls.join("\n") + "\n" + jobs_dsls.join("\n")
	jobDsl removedConfigFilesAction: 'DELETE', removedJobAction: 'DELETE', removedViewAction: 'DELETE', sandbox: true, scriptText: "$final_dsl"
}