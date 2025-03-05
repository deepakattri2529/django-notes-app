@Library("jenkins-shared-lib") _
pipeline{
    
    agent { label "vinod"}
    
    stages{
        
        stage("hello"){
            steps{
                script{
                    deep()
                }
            }
        }
        stage("code"){
          steps {
              script{
              clone("https://github.com/deepakattri2529/django-notes-app.git","main")
              }
          }  
        }
        stage ("build"){
            steps {
                script{
                docker_build("notes-app","latest","deepakattri0007")
                }
            }
        }
        stage ("Docker push"){
            steps {
                script{
                    docker_push("notes-app","latest","deepakattri0007")
                }
            }
        }
        stage("deploy"){
            steps {
                sh "docker run -d -p 8000:8000 notes-app:latest"
            }
        }
    }
}
