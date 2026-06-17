pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Pavans-24/bit185.git'
            }
        }
        stage('Build WAR Artifact') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Manual Server Copy & Mode Configuration') {
            steps {
                sh '''
                    sudo cp target/185_webapp.war /opt/tomcat/webapps/
                    sudo chmod 755 /opt/tomcat/webapps/185_webapp.war
                    sudo sh /opt/tomcat/bin/shutdown.sh || true
                    sudo sh /opt/tomcat/bin/startup.sh
                '''
            }
        }
    }
}

