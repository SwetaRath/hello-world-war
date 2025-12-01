pipeline {
    agent none

    stages {

        stage('hello-world-war') {
            parallel {

                stage('Checkout') {
                    agent { label 'Java' }
                    steps {
                        sh "rm -rf hello-world-war"
                        sh "git clone https://github.com/SwetaRath/hello-world-war.git"
                    }
                }

                stage('Build') {
                    agent { label 'Java' }
                    steps {
                        dir('hello-world-war') {
                            sh "mvn clean package"
                        }
                    }
                }

                stage('Deploy') {
                    agent { label 'Java' }
                    steps {
                        echo "Deploying the application"
                        sh "sudo cp /home/slave1/workspace/hello-world-war/target/hello-world-war-1.0.1.war /opt/apache-tomcat-10.1.49/webapps/"
                    }
                }

            }
        }

    }
}
