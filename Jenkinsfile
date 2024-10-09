pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                script {
                    catchError(buildResult: 'SUCCESS') {
                        sh 'docker stop samplerunning || true'
                        sh 'docker rm samplerunning || true'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                build job: 'BuildSampleApp'
            }
        }

        stage('Results') {
            steps {
                build job: 'TestSampleApp'
            }
        }
    }
}
