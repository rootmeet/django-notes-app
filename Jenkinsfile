@Library("Shared") _
pipeline{
    
    agent { label "vinod"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
               script{
                clone("https://github.com/rootmeet/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("note-app","latest","sanjeevrisbud")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("note-app","latest","sanjeevrisbud")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
