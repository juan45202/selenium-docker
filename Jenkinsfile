pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Build Jar') {
            steps {
                //sh
                chmod "mvn clean package -DskipTests"
            }
        }
        stage('Build Image') {
            steps {
                //sh
                chmod "docker build -t='jjrm8/selenium-docker' ."
            }
        }
        stage('Push Image') {
            steps {
			    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    //sh
			        chmod "docker login --username=${user} --password=${pass}"
			        chmod "docker push jjrm8/selenium-docker:latest"
			    }
            }
        }
    }
}