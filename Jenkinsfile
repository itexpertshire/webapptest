
pipeline {
    agent {
        docker {
            image 'openkbs/jre-mvn-py3' 
            args '-u 0 --name=mycontainer -v /home/bitnami/GitHub/webapptest/jenkins/scripts:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
      stage('Python Install') {
            steps {
                sh './jenkins/scripts/pythoninstall.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
