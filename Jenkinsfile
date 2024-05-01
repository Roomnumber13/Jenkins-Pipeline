pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "https://github.com/Roomnumber13/Deakin-Unit-Page.git"
        TESTING_ENVIRONMENT = "Stranger Things"
        PRODUCTION_ENVIRONMENT = "Rajkumar Rajendran"
    }

    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [
                    [name: '*/main']
                ], extensions: [], userRemoteConfigs: [
                    [url: 'https://github.com/Roomnumber13/Jenkins-Pipeline.git']
                ])
            }
        }
        stage('Build') {
            steps {
                echo "fetch the source code from the $DIRECTORY_PATH specified by the environment variable"
                echo "compile code and generate any necessary artifacts"
                echo "Use Maven to compile and package your code"
            }
        }
        stage("Test") {
            steps {
                echo "nUnit used for unit and integration test"
                echo "unit tests successful"
                echo "integration tests successful"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit...'
                echo 'Running integration tests with Selenium....'
            }
            post {
                success {
                    // Send email notification on successful pipeline completion
                    emailext(to: "rajkumar.rajendran197@gmail.com",
                             subject: "Successful pipeline",
                             body: "Unit & Integration is successful!",
                             attachLog: true)
                }
                failure {
                    // Send email notification on pipeline failure
                    emailext(to: "rajkumar.rajendran197@gmail.com",
                             subject: "Failed pipeline",
                             body: "The test has failed. Please check!",
                             attachLog: true)
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Integrating SonarQube for code analysis with Jenkins....'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP....'
            }
            post {
                success {
                    // Send email notification on successful pipeline completion
                    emailext(to: "rajkumar.rajendran197@gmail.com",
                             subject: "Successful pipeline",
                             body: "The security scan is successful!",
                             attachLog: true)
                }
                failure {
                    // Send email notification on pipeline failure
                    emailext(to: "rajkumar.rajendran197@gmail.com",
                             subject: "Failed pipeline",
                             body: "The security scan has failed. Please check!",
                             attachLog: true)
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to staging server using AWS CodeDeploy....'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment..'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to production server using AWS CodeDeploy...'
            }
        }
    }
}
