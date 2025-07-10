pipeline {
    agent any
 
 
    tools {
        // Install the Maven version configured as "M398" and add it to the path.
        maven "M398"
    }
 
 
    stages {
        stage('Echo Version') {
            steps {
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }
        stage('Build') {
            steps {
                // Get some code from a Gitea repository specifying the main branch
                //git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Shravya-Devtools/jenkins-hello-world.git'
                // Run Maven Package command and skip tests
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Test') {
            steps {
                script{
                    for(int i = 0; i < 60; i++) {
                        echo "${i+1}"
                        sleep 1
                    }
                    sh 'mvn test'
                }
            }
        }
    }
}
