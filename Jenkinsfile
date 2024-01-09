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
        stage('Checkout Github') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [],
                userRemoteConfigs: [[credentialsId: GITCREDENTIAL, url: GITWEBADD]]])
            }
        
        
            post {
        
                failure {
                    echo 'Repository clone failure'
                }
                success {
                    echo 'Repository clone success'
                }
            }
        }
        
        stage('code build'){
            steps {
                sh "mvn clean package"
            }
        
        }
        stage('image build'){
            steps {
                sh "docker build -t ${DOCKERHUB}:${currentBuild.number} ."
                sh "docker build -t ${DOCKERHUB}:latest ."

            }
        }
        
        stage('image push'){
            steps{
                sh "docker push ${DOCKERHUB}:${currentBuild.number}"
                sh "docker push ${DOCKERHUB}:latest"
            }
            
            post {
                failure {
                    echo 'docker image push failure'
                    sh "docker image rm -f ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker image rm -f ${DOCKERHUB}:latest
                }
                
                 success {
                    echo 'docker image push success'
                    sh "docker image rm -f ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker image rm -f ${DOCKERHUB}:latest"
                }

            }
        
        
        }
        stage(){
        
        
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
