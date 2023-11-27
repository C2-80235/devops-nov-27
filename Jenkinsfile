pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/C2-80235/devops-nov-27.git'
            }
        }
        stage ('docker build image') {
              steps {
                  sh '/usr/bin/docker image build -t shnk/exam-image .'
              }
          }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_eB-g-nh0WP5R_EiJ7gKVISmne38 | /usr/bin/docker login -u shnk --password-stdin'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push shnk/exam-image'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm exam-service'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name exam-service -p 9876:80 --replicas 5 shnk/exam-service'
            }
        }
    }
}
