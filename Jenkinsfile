pipeline {
  agent any
	stages {
    stage('Cloning Git') {
        steps {
          sh 'echo "Connecting to the source code repository ..."'
          sh "git init /var/lib/jenkins/workspace/${env.JOB_NAME}"
          sh "git config remote.origin.url https://github.com/postgres/postgres.git refs/heads/*:refs/remotes/origin/*"
          sh "git fetch origin"
          sh "git checkout REL_12_STABLE"
        }
    }
    stage('Build') {
      agent
    	{
  	    docker {
          image 'centos:7'
          args  '-v /tmp:/tmp'
        }
      }
      steps {
          sh pwd
      }
    }
    stage('Test') {
      steps {
          echo "Test Process"
      }
    }
    stage('Deploy') {
      steps {
          echo "Deployment Process"
      }
    }
	}
}
