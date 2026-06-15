@Library("shared") _
pipeline {
    agent { label 'vinod' }

    stages {
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }

        stage('code') {
            steps {
                script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }
                
            }
        }

        stage('build') {
            steps {
               
                script{
                    docker_build("notes-app","latest","vijaybadsila65")
                }
            }
        }

        stage('push to docker hub') {
            steps {
                script{
                    docker_push("notes-app","latest","vijaybadsila65")
                }
            }
        }

        stage('deploy') {
            steps {
                echo 'deploy stage'

                sh 'docker compose up -d || docker-compose up -d'
            }
        }
    }
}
