pipeline {
    agent {
        label 'default'
    }

    parameters {
        string(name: 'NAME', defaultValue: 'World', description: 'Name to greet')
    }
    
    triggers {
      pollSCM 'H/3 * * * *'
    }
    environment {
        GIT_URL = 'https://github.com/Chernozem97/Sberbank_Homework.git'
    }

    stages{
        stage('Greet') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]){
                    def name = params.NAME
                    def credentials = "Username: ${GIT_USERNAME}\nPassword: ${GIT_PASSWORD}"
                    writeFile file: 'result.txt', text: "hello ${name}\n${credentials}"
                    }
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
