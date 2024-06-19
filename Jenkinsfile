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
        MY_CRED = crendentials('github-credentials')
    }

    stages{
        stage('Greet') {
            steps {
                script {
                        def name = params.NAME
                        def credentials = "Username: ${MY_CRED_USR}\nPassword: ${MY_CRED_PSW}"
                        writeFile file: 'result.txt', text: "hello ${name}\n${credentials}"
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
