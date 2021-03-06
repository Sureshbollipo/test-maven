pipeline {
  agent {
    kubernetes {
      yaml """\
        apiVersion: v1
        kind: Pod
        metadata:
          labels:
            jenkins: slave
        spec:
          containers:
          - name: maven
            image: maven:alpine
            command:
            - cat
            tty: true
        """.stripIndent()
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
          sh 'java -version'
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