pipeline {
    agent any
    stages{
        stage("git clone"){
            steps{
                git branch: 'main', 
                credentialsId: 'github-creds', 
                url: 'https://github.com/shaliniche-code/flask-devops-app.git'
            }
        }   
        stage("listing"){
            steps{
                sh 'ls'
        }
        }
         stage("docker build"){
             steps{
                 sh 'docker build -t flask_app_v2 .'
             }
         }
         stage("Remove Old Container") {
           steps {
               sh 'docker rm -f flask_container_v2 || true'
    }
}
         stage("docker run"){
             steps{
                 sh 'docker run -d --name flask_container_v2 -p 5000:5000 flask_app_v2'
             }
         }
        
    }
}
