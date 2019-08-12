pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Automation checkout/Test') {
            if ("${runSmokeTest}" == 'false'){
                echo 'Skip Automation Test'
            }else{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: "${RemoteConfig}"]]])
                sh "mvn test -PSmoke"
             }        
        }

    }
}
