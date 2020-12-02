pipeline {
    agent { label 'buildah' }

    stages {
        stage ('Build') {
            steps {
                sh 'yum -y install gcc*'
            }
        }
        stage ('Build1') {
            steps {
                sh 'g++ -o Hello HelloPlanet.cpp'
                sh './Hello'
            }
        }
    }
}
