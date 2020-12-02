pipeline {
    agent { label 'buildah' }
	
	environment {
        DOCKER_REGISTRY = 'nexus.nos-lab.io:8446'
        IMAGE_DESTINATION = "${DOCKER_REGISTRY}/nos/nos-coverity-gcc:test"
    }

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
        stage ('Run'){
            steps {
                sh './Hello'
            }
        }       
    }
}
