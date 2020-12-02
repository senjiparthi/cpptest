pipeline {
    agent { label 'buildah' }
	
	environment {
        DOCKER_REGISTRY = 'nexus.nos-lab.io:8446'
        IMAGE_DESTINATION = "${DOCKER_REGISTRY}/nos/nos-coverity-gcc:test"
    }

    stages {
        stage ('Build') {
            steps {
                sh 'yum -y install gcc*'
                sh 'yum -y install man-pages'
                sh 'gcc –-version'
            }
        }
    }
}
