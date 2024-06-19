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


        stage('Greet') {
            steps {
                script {
                    def name = params.NAME
                    writeFile file: 'result.txt', text: "hello ${name}"
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
