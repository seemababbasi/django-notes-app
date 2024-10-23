@Library("Shared") _

pipeline {
    agent { label "slave-2" }

    stages {
        stage('Clone the code') {
            steps {
                script{
                clone("https://github.com/seemababbasi/django-notes-app.git", "main")
                }
            
           }    
        }

        stage( 'image' ){
            steps{
                script{
                    push()
                }
            }
        }
        
        stage('Build the code') {
            steps {
                script{
                    build("notes-app", "latest", "seemababbasi94380")    
                }
            }
        }
        
        stage('Pushing the code to DockerHub') {
            steps {
                script{
                    dockerhub("notes-app", "latest", "seemababbasi94380")
                        }
                   }
            }
        
         stage('Deploy') {
            steps {
                script{
                    deploy()
                  }
            }    
       }
    }

}
