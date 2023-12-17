pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS= credentials('jen-lab')
    }
    stages {
        stage('CI') {
            steps {

               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ahmedali --password-stdin"
               sh "pwd"
               sh "docker build -f dockerfile -t yourapp ."
               sh "docker push yourapp"
                }
            }
        
        stage('CD') {
            steps {
               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ahmedali --password-stdin"
               sh "docker run -d -p 3000:3000 yourapp"
            }
        }
    }
        
    }
