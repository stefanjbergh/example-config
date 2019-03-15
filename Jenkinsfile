pipeline {
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
                    app = docker.build("crud-springboot-dynamodb/hellonode")
                }
            } 
         
        }
}
