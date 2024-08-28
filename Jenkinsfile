pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Stage 1: Build'
                    echo 'Task: Build the code using build automation tool'
                    echo 'Tool: Maven'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Stage 2: Unit and Integration Tests'
                    echo 'Task: Run unit tests and integration tests'
                    echo 'Tools: JUnit, TestNG, Selenium'
                    
                    // Capture stage-specific log
                    def logFile = 'unit-integration-tests.log'
                    writeFile file: logFile, text: "Unit and Integration Tests stage log\n${currentBuild.rawBuild.getLog().join('\n')}"
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
                            attachmentPattern: 'unit-integration-tests.log'
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
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Stage 4: Security Scan'
                    echo 'Task: Scan the code for security vulnerabilities'
                    echo 'Tool: Snyk'
                    
                    // Capture stage-specific log
                    def logFile = 'security-scan.log'
                    writeFile file: logFile, text: "Security Scan stage log\n${currentBuild.rawBuild.getLog().join('\n')}"
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
                            attachmentPattern: 'security-scan.log'
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
}
