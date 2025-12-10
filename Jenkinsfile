pipeline {
    agent any

    parameters {
        string(name: 'mcd1', defaultValue: '', description: 'Enter your name')
        booleanParam(name: 'Boolean', defaultValue: true, description: 'Enable or disable')
        choice(name: 'mcd2', choices: ['install', 'package', 'compile'], description: 'select the choice')
    }

    stages {
        stage('checkout') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'c9a17574-89f2-4a43-8c65-205c91c2ae8f',
                        usernameVariable: 'admin',
                        passwordVariable: 'admin_password'
                    ),
                    sshUserPrivateKey(
                        credentialsId: 'cda79cd0-7253-42ce-b954-9ca00fdb0f62',
                        keyFileVariable: 'KEY_FILE',
                        usernameVariable: 'SSH_USER'
                    )
                ]) {
                    sh "rm -rf hello_world_war"
                    sh "git clone https://github.com/SwetaRath/hello-world-war.git"
                }
            }
        }

        stage('build') {
            steps {
                sh "mvn $mcd2"
            }
        }

        stage('deploy') {
            steps {
                sh "sudo cp /home/slave1/workspace/hello_world_war/target/hello_world_war_1.0.1.war /opt/apache-tomcat-10.1.49/webapps/"
            }
        }
    }
}
