pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Stage 1: Build'
                    echo 'Task: Build the code using build automation tool'
                    echo 'Tool: Maven'
                    sh 'echo "Build stage log" > build.log'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Stage 2: Unit and Integration Tests'
                    echo 'Task: Run unit tests and integration tests'
                    echo 'Tools: JUnit, TestNG, Selenium'
                    sh 'echo "Unit and Integration Tests stage log" > unit-integration-tests.log'
                }
            }
            post {
                always {
                    script {
                        emailext(
                            to: 'corrinaglover@gmail.com',
                            subject: "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} - Unit and Integration Tests ${currentBuild.result}",
                            body: """
                            Stage: Unit and Integration Tests
                            Build Status: ${currentBuild.result}
                            Job: ${env.JOB_NAME}
                            Build Number: ${env.BUILD_NUMBER}

                            Please find the logs attached.
                            """,
                            attachmentsPattern: 'unit-integration-tests.log'
                        )
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Stage 3: Code Analysis'
                    echo 'Task: Analyze code quality and adherence to industry standards'
                    echo 'Tool: SonarQube'
                    sh 'echo "Code Analysis stage log" > code-analysis.log'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Stage 4: Security Scan'
                    echo 'Task: Scan the code for security vulnerabilities'
                    echo 'Tool: Snyk'
                    sh 'echo "Security Scan stage log" > security-scan.log'
                }
            }
            post {
                always {
                    script {
                        emailext(
                            to: 'corrinaglover@gmail.com',
                            subject: "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} - Security Scan ${currentBuild.result}",
                            body: """
                            Stage: Security Scan
                            Build Status: ${currentBuild.result}
                            Job: ${env.JOB_NAME}
                            Build Number: ${env.BUILD_NUMBER}

                            Please find the logs attached.
                            """,
                            attachmentsPattern: 'security-scan.log'
                        )
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Stage 5: Deploy to Staging'
                    echo 'Task: Deploy the application to a staging environment'
                    echo 'Tool: AWS EC2 instance'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Stage 6: Integration Tests on Staging'
                    echo 'Task: Run integration tests in the staging environment'
                    echo 'Tool: Selenium'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Stage 7: Deploy to Production'
                    echo 'Task: Deploy the application to the production server'
                    echo 'Tool: AWS EC2 instance'
                }
            }
        }
    }

    post {
        always {
            script {
                sh 'echo "Overall build log" > overall-build.log'
                emailext(
                    to: 'corrinaglover@gmail.com',
                    subject: "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} - ${currentBuild.result}",
                    body: """
                    Build Status: ${currentBuild.result}
                    Job: ${env.JOB_NAME}
                    Build Number: ${env.BUILD_NUMBER}

                    Please find the build log attached.
                    """,
                    attachmentsPattern: 'overall-build.log'
                )
            }
        }
    }
}
