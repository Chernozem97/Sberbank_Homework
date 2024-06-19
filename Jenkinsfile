pipeline {
    agenх {
        label 'default'
    }

    parameters {
        string(name: 'NAME', defaultValue: 'World', description: 'Name to greet')
    }

    environment {
        GIT_URL = 'https://github.com/Chernozem97/Sberbank_Homework.git'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: "${env.GIT_URL}", branch: 'main'
            }
        }

        stage('Greet') {
            steps {
                script {
                    def name = params.NAME
                    writeFile file: 'result.txt', text: "Hell\o ${name}"
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'result.txt', onlyIfSuccessful: true
        }
    }
}
