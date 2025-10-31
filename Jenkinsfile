@Library("SharedLibs") _
pipeline{
    agent any
    
    stages{
        stage("Hello"){
            steps{
                script{
                  hello("night")   
                }
            }
        }
        
        stage("Clone"){
            steps{
                script{
                    clone("https://github.com/biswarupgh0sh/django-notes-app-for-jenkins-cicd.git", "main")
                }
            }
        }
        
        stage("Build"){
            steps{
                script{
                    build("notes-app", "latest")
                }
            }
        }
        stage("Pushing to dockerhub"){
            steps{
                script{
                    pushToDockerHub("notes-app", "latest")
                }
            }
        }

        stage("Deploying"){
            steps{
                echo "deploying the app"
                sh "docker compose down"
                sh "docker-compose up -d"
                echo "app is deployed"
            }
        }
    }
    
    
    post {
        success {
            echo "pipeline successfull"
        }
        failure{
            echo "pipeline failed"
        }
    }
}
