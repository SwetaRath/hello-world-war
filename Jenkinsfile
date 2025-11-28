pipeline {
    agent none

    stages {

        stage('hello-world-war') {
            parallel {

                stage('Checkout') {
                    steps {
                        sh "rm -rf hello-world-war"
                        sh "git clone https://github.com/SwetaRath/hello-world-war.git"
                    }
                }

                stage('Build') {
                    steps {
                        dir('hello-world-war') {
                            sh "mvn clean package"
                        }
                    }
                }

                stage('Deploy') {
                    steps {
                        echo "Deploy the application"
                        dir('hello-world-war') {
                            sh "mvn clean package"
                        }
                    }
                }

            }
        }

    }
}
