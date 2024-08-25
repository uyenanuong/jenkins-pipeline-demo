pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Use Maven to build the project
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Use a test automation tool like JUnit for Unit Tests and Selenium for Integration Tests
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                // Use a code analysis tool like SonarQube
                sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running Security Scan...'
                // Use a security scanning tool like OWASP Dependency-Check
                sh 'dependency-check --project my-app --scan ./'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to a staging server, e.g., AWS EC2
                sh 'scp target/my-app.war user@staging-server:/var/www/html/'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run integration tests on the staging server
                sh 'mvn verify -Dtest=*IT'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy to a production server, e.g., AWS EC2
                sh 'scp target/my-app.war user@production-server:/var/www/html/'
            }
        }
    }
    post {
        always {
            mail to: 'iwsj4redvelvet@gmail.com',
                 subject: "Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Pipeline Status: ${currentBuild.currentResult}\n\n${env.BUILD_URL}",
                 attachLog: true
        }
    }
}
