pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Kururyk1/devops-midterm.git'
            }
        }

        stage('Build JAR') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh '''
                curl -u admin:admin123 \
                --upload-file target/demo-0.0.1-SNAPSHOT.jar \
                http://nexus:8081/repository/maven-releases/demo-0.0.1-SNAPSHOT.jar
                '''
            }
        }
    }
}
