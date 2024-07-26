pipeline{
    agent any
    stages{
         stage("GitHub checkout....") {
            steps {
                script {
 
                    git branch: 'master', url: 'https://github.com/lyday25/flask.git' 
                }
            }
        }
        stage("Build docker connecting....."){
            steps{
                sh 'printenv'
                sh 'git version'
                sh 'docker build . -t lyday25/f-app1.0'
            }
        }
         stage("push image to DockerHub"){
            steps{

               script {
                  
                 withCredentials([string(credentialsId: 'DockerID', variable: 'DockerID')]) {
                    sh 'docker login -u lyday25 -p ${DockerID}'
            }
              sh 'docker push lyday25/f-app1.0:latest'
            }
        }
    }
    }
}
