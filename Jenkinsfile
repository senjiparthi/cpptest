pipeline {
    agent any

    stages {
        stage ('Checkout'){
            steps {
                checkout scm
            }
        }
        stage ('Build') {
            steps {
                sh 'g++ -o Hello HelloPlanet.cpp'
            }
    }
        stage ('Test1'){
            steps {
                sh 'pwd'
            }
        }

}
}
