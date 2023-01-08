pipeline{

	agent any
	tools {
		maven 'maven'
	}
  parameter([
    choice(
      choices: ['project-a', 'project-b'],
      name: "project"
    )
  }
	stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/apache-maven-3.8.5"
            }
	}
		stage('Checkout') {
			steps {
			checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-access', url: 'https://github.com/SNazeer786/simple-java-maven-app.git']]])
			}
		}
    stage ('dir') {
      steps {
      sh 'cd $project'
      }
    }
		stage ('Build') {
			steps {
			sh 'mvn -B -DskipTests clean package'		
			}
		
		}
	
	}
}
