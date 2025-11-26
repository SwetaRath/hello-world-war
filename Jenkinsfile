pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh  "rm -rf hello-world-war"
                sh "git clone https://github.com/SwetaRath/hello-world-war.git"
            }
        }
    }
stages {
        stage('Build') {
            steps {
                dir('hello-world-war')
{
                sh  "mvn clean package"
           }
}
}
}
stages {
        stage('Deploy') {
            steps {
           echo "Deploy the application"
                sh  "mvn clean package"
           }
}
}
}
