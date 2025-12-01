pipeline {
    agent none
   stages {

        stage('hello-world-war') {
            parallel {

                stage('Checkout') {
                    agent { label ' Java ' }
                    steps {
                        sh "rm -rf hello-world-war"
                        sh "git clone https://github.com/SwetaRath/hello-world-war.git"
                    }
                }

                stage('Build') {
                    agent { label ' Java ' }
                    steps {
                       
                            sh "mvn clean package"
                        
                    }
                }

                stage('Deploy') {
                    agent { label ' Java ' }
                    steps {
                        echo "Deploy the application"
                            sh '  cp /home/slave1/workspace/hello_world_war/target/hello-world-war-1.0.1.war /home/opt/apache-tomcat-10.1.49/webapps '
                        }
                    }
                }

            }
        }

    }

