pipeline{
agent any
environment {
  java_home = "/usr/java"
}
tools {
  maven 'mymaven'
}
triggers {
  cron '*/5 * * * *'
}
stages {
  stage('gitclone') {
    steps {
      // One or more steps need to be included within the steps block.
	 git 'https://github.com/sivaji348/addressbook.git'
    }
  }
  stage('compile') {
  steps {
    // One or more steps need to be included within the steps block.
	sh 'mvn compile'
  }
}
  stage('review') {
  steps {
    // One or more steps need to be included within the steps block.
	sh 'mvn pmd:pmd'
	recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
  }
}
stage('test') {
  steps {
    // One or more steps need to be included within the steps block.
	sh 'mvn test'
	junit 'target/surefire-reports/*.xml'
  }
}
stage('package') {
  steps {
    // One or more steps need to be included within the steps block.
	sh 'mvn package'
  }
}

}

}
