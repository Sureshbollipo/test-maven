pipeline {
  agent {
    kubernetes {
      defaultContainer 'maven'
      yamlFile 'k8s-maven-pod.yaml'
    }
  }
  stages {
	stage ('Code Checkout') {
		steps{
			checkout scm			
		}
	}
    stage('Build') {
		steps {
			sh 'mvn package'
		}
    }
	stage ('Code Testing') {
		steps{
			sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
		}
	}
  }
}