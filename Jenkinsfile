pipeline {
    // agent { label 'java' }
    agent any
    parameters {
        string(name: 'mcd1', defaultValue: '', description: 'Enter your name')
        booleanParam(name: 'Boolean', defaultValue: true, description: 'Enable or disable')
        choice(name: 'mcd2', choices: ['install', 'package', 'compile'], description: 'select the choice')
    }
    stages {
        stage('checkout') {
            // agent { label 'java' }
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'cce2c98e-78c8-4883-b00b-c393c23f7713',
                    usernameVariable: 'admin',
                    passwordVariable: 'admin_password'
                ),
                    sshUserPrivateKey(
    credentialsId: 'cda79cd0-7253-42ce-b954-9ca00fdb0f62',
    keyFileVariable: 'KEY_FILE',
    usernameVariable: 'SSH_USER'
               )
    ]) {
                    sh "rm -rf hello-world-war"
                    sh "https://github.com/SwetaRath/hello-world-war.git"
                }
            }
        }
        stage ('build') {
            steps {
                sh "mvn $mcd1 $mcd2"
                }
        }
        stage ('deploy') {
            steps {
                sh "sudo cp ${env.WORKSPACE}/target/hello-world-war-1.0.1.war /opt/apache-tomcat-10.1.49/webapps/"
            }
        }
    }
}
