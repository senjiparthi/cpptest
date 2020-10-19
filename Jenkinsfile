pipeline {
    agent any

    stages {
        stage ('Checkout'){
            steps {
                checkout scm
            }
        }
        stage ( 'Build' ) {
            steps {
                sh 'ls'
            }
    }
        stage ('Build'){
            steps {
                sh 'pwd'
            }
        }

}
}