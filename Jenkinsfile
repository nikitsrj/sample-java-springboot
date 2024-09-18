pipeline {
    agent any
    stages {
        // stage('Checkout Code') {
        //     steps {
        //          git branch: 'main', url: 'https://github.com/nikitsrj/sample-java-springboot.git'
        //     }
        // }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Run Application') {
            steps {
                sh 'JENKINS_NODE_COOKIE=dontKillMe nohup java -jar target/hello-world-webapp-1.0-SNAPSHOT.jar --server.port=80 > app.log 2>&1 & '
            }
        }
    }
    post {
        success {
            echo 'Build and application run successfully!'
        }
        failure {
            echo 'Build or application run failed.'
        }
    }
}
