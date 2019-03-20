pipeline {
    def app
    agent any
    tools {
            maven 'mavenTool'
            jdk 'JDK8u'
        }
        stages {
            stage ('git-clone') {
                steps {
                    git branch: 'master', url: 'https://github.com/raviydevops/crud-springboot-dynamodb'
			/* checkout scm */
                }
            }

            stage ('mavenCIbuild') {
                steps {
                    sh 'mvn clean package'
                    
                }
            }
            stage ('Build image') {
                steps {
                    app = docker.build("rajesh412/hellonode")

                }
            } 
            stage('Push image') {

                docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                   app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                }   
                    echo "Trying to Push Docker build to Dockerhub"
            }
        }
}
