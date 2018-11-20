# seed_job
Repository to hold the seed job dsl script and list of jobs to be created. 

Seed Job is a JobDSL plugin concept. Its a job which can create and configure other jobs in jenkins. 

This Job is made generic to read a yaml file which list all the required jobs that required to be created. 
Every entry in the yaml points to the Jenkinsfile and a repository where the Jenkinsfile exists.