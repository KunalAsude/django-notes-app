@Library("shared") _
pipeline {
    
    agent {label "agent"}
    stages {
        stage("hello"){
            steps{
                script{
                    hello()
                } 
            }
        }
        stage('Clone') {
            steps {
                script{
                clone('https://github.com/KunalAsude/django-notes-app.git','main')
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script{
                    docker_build("notes-app","latest","kunalasude")
                }
            }
        }
        
        stage('Push image to docker hub') {
            steps {
                script{
                    docker_push("notes-app","latest","kunalasude")
                }
            }
        }
        stage('Run Container') {
            steps {
                script{
                    docker_compose()
                }
            }
        }
    }
}
