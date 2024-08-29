pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Building the project....'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Performing code analysis...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Performing security scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploying to staging server...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploying to production server...'
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/build.log', allowEmptyArchive: true
                    echo "Pipeline completed successfully!"
                    emailext (
                        to: 'yohan20050917@gmail.com',
                        subject: "Pipeline Passed: ${env.JOB_NAME} Build #${env.BUILD_NUMBER}",
                        body: """The pipeline has completed successfully.
                                 Build number: ${env.BUILD_NUMBER}\n\n
                                 Check Jenkins for details: ${env.BUILD_URL}""",
                        attachLog: true
                    )
                }
                failure {
                    echo "Pipeline failed. Please check the logs."
                }
            }
        }
    }
}
