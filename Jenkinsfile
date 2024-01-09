pipeline {
    agent any
    
    tools {
        maven 'my_maven'
    }
    
    environment {
        GITNAME = 'skystar200'              
        GITEMAIL = 'skystar20095@gmail.com' 
        GITWEBADD = 'https://github.com/skystar200/sb_code.git'
        GITSSHADD = 'git@github.com:skystar200/sb_code.git'
        GITCREDENTIAL = 'git_cre' 
    }
        
    
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
    }
}
