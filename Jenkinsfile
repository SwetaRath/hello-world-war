pipeline {
    agent { label 'Java' }
    stages {
        stage('Checkout') {
            steps {
                sh  "rm -rf hello-world-war"
                sh "git clone https://github.com/SwetaRath/hello-world-war.git"
            }
        }
        stage('Build') {
            steps {
                dir('hello-world-war')
{
                sh  "mvn clean package"
           }
}
}
         stage('Deploy') {
            steps {
           echo "Deploy the application"
                sh  "mvn clean package"
           }
}
}
}
