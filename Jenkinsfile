pipeline {
  agent any
	stages {
    stage('Cloning Git') {
      steps {
        sh 'echo "Connecting to the source code repository ..."'
        sh "git init /var/lib/jenkins/workspace/${env.JOB_NAME}"
        sh "git fetch --tags --progress https://github.com/postgres/postgres.git +refs/heads/*:refs/remotes/origin/*"
        sh "git checkout -b origin/REL_12_STABLE"
        sh "git pull master origin"
      }
    }
    stage('Build') {
      agent
    	{
  	    docker {
          image 'centos:7'
        }
      }
      steps {
          sh 'pwd'
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
