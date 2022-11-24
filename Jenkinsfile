pipeline {
    agent any
     tools { 
    gradle "Gradle - 6"
  }
    stages {
        stage ("Clone Repo"){
            steps {
            git 'https://github.com/jnkiarie/java-todo.git'
            }
        }
        stage ('Build Project'){
            steps{
                 sh 'gradle build'
            }
        }
        stage('Test Project'){
            steps{
                sh 'gradle test'
            }
        }
        
        stage('Deploy to Heroku') {
            steps {
            withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
            sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/murmuring-spire-24159.git master'
    }
  }
}

    }
}