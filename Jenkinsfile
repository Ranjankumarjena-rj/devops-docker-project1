pipeline{
    agent any
    tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
    stages{
        stage ("checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/Ranjankumarjena-rj/devops-docker-project1.git'
            }
        }
        stage ("build"){
            steps{
              sh 'mvn clean package'
        }
      }
        stage ("docker build"){
          steps{
              sh 'docker build -t ranjankumarjena/docker-project:latest .'
          }
          }
         stage ("docker push"){
             steps{
                 withCredentials([string(credentialsId: 'pass', variable: 'password')]) {
                 sh "docker login -u ranjankumarjena -p ${password}"
                 
                 sh 'docker push ranjankumarjena/docker-project:latest'
               }
             }
         }
    }
}
