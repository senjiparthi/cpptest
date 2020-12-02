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
    
    stages {
        stage ('Coverity Scan'){
            steps {
                sh './cov-build --dir /var/jenkins_home/workspace/testcpp/report/ g++ -o Hello /var/jenkins_home/workspace/testcpp/HelloPlanet.cpp'
                sh './cov-analyze --dir /var/jenkins_home/workspace/testcpp/report/'
            }
        }
        stage ('SonarQube Scan'){
            steps {
                sh 'build-wrapper --out-dir bw-outputs ./Hello' 
                sh 'sonar-scanner' 
            }
        }
        stage ('Nexus Archival'){
	      environment {
                NEXUS_TOKEN = credentials('NEXUS-CRED')
              }	
              steps {
                sh 'curl -u $NEXUS_TOKEN_USR:$NEXUS_TOKEN_PSW --upload-file Hello https://nexus.avionics.io:8443/repository/cpp/Hello'
            }
        }


}
}
