pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-21'
        PATH = "${env.JAVA_HOME}\\bin;${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Praveen2197/Alldevice2025automation.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Run Multi-Device Test') {
            steps {
                bat 'mvn test -DsuiteXmlFile=testng.xml'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: '**/target/**/*.log, **/videos/*.mp4', fingerprint: true
        }
    }
}
