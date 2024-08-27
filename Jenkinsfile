pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
                echo 'Task: Compile and package the code.'
                echo 'Tool: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests'
                echo 'Task: Run unit tests to ensure code functions as expected, and run integration tests to ensure different components work together.'
                echo 'Tool: JUnit'
            }
            post {
                always {
                    mail to: "nguyenchuong27042005@gmail.com",
                         subject: "Jenkins: Unit and Integration Tests - ${currentBuild.currentResult}",
                         body: "Unit and Integration Tests stage has finished with status: ${currentBuild.currentResult}",
                         attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
                echo 'Task: Analyze the code to ensure it meets industry standards.'
                echo 'Tool: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
                echo 'Task: Perform a security scan to identify vulnerabilities.'
                echo 'Tool: Snyk'
            }
            post {
                always {
                    mail to: "nguyenchuong27042005@gmail.com",
                         subject: "Jenkins: Security Scan - ${currentBuild.currentResult}",
                         body: "Security Scan stage has finished with status: ${currentBuild.currentResult}",
                         attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
                echo 'Task: Deploy the application to a staging environment.'
                echo 'Tool: Ansible'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
                echo 'Task: Run integration tests in the staging environment to ensure the application functions as expected in a production-like environment.'
                echo 'Tool: JUnit'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
                echo 'Task: Deploy the application to the production environment.'
                echo 'Tool: Ansible'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for details.'
        }
    }
}
