
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
                def buildStatus = currentBuild.result ?: 'SUCCESS'
                def subject = "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} - ${buildStatus}"
                def body = """
                Build Status: ${buildStatus}
                Job: ${env.JOB_NAME}
                Build Number: ${env.BUILD_NUMBER}
                """

                // Send an email
                mail(
                    to: 'corrinaglover@gmail.com',
                    subject: subject,
                    body: body
                 )
            }
        }
    }
}
