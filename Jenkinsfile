pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh 'mvn clean package'

            }
        }
        stage('test') {
            steps {
                echo 'Testing..'
		sh 'mvn test'
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying....'
		sshagent(['admin1']) {
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkins-pipe/target/webapp-0.2.war centos@35.175.135.97:/home/centos/apache-tomcat-10.0.27/webapps"
		 }
            }
        }
    }
}
