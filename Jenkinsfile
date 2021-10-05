pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                git 'https://github.com/raj14ar/hello-world.git'
            }
        }
        stage('build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('deploy') {
            steps {
                sshagent(['aws_user_deploy']) {
                    sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/demo_pipeline/webapp/target/webapp.war ec2-user@35.154.224.182:~/tomcat9/webapps"
                }
            }
        }
    }
}
