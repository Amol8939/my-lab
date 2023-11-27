pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/Amol8939/my-lab.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_KtjNYjOosyxxsdiFmXAHJUkGSsM | /usr/bin/docker login -u amol1701 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t amol1701/my-lab-image .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push amol1701/my-lab-image'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm nginx-service'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --replicas 5 --name nginx-service -p 9876:80 amol1701/my-lab-image'
            }
        }
    }
}   
