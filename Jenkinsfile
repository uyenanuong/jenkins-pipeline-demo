pipeline {     
    agent any     
    stages {         
        stage("Build") {             
            steps {                 
                echo "Building the code using Maven" 
            } 
        } 
         
        stage("Unit and Integration Tests") { 
            steps {                 
                echo "Running unit tests with JUnit and integration tests with Selenium" 
            }             
            post {                 
                success {                     
                    emailext (
                        to: "iwsj4redvelvet@gmail.com",                         
                        subject: "Unit and Integration Tests Stage Success",                         
                        body: "The Unit and Integration Tests stage has completed successfully!",                         
                        attachLog: true 
                    )                 
                }                 
                failure {                     
                    emailext (
                        to: "iwsj4redvelvet@gmail.com",                         
                        subject: "Unit and Integration Tests Stage Failure",                         
                        body: "The Unit and Integration Tests stage has failed!",                         
                        attachLog: true 
                    ) 
                } 
            } 
        } 
 
        stage("Code Analysis") { 
            steps { 
                echo "Analyzing code quality with SonarQube" 
            } 
        } 
 
        stage("Security Scan") { 
            steps { 
                echo "Performing security scan using OWASP ZAP" 
            }             
            post {                 
                success {                     
                    emailext (
                        to: "iwsj4redvelvet@gmail.com",                         
                        subject: "Security Scan Stage Success",                         
                        body: "The Security Scan stage has completed successfully!",                         
                        attachLog: true 
                    )                 
                }                 
                failure {                     
                    emailext (
                        to: "iwsj4redvelvet@gmail.com",                         
                        subject: "Security Scan Stage Failure",                         
                        body: "The Security Scan stage has failed!",                         
                        attachLog: true 
                    ) 
                } 
            } 
        } 
 
        stage("Deploy to Staging") { 
            steps { 
                echo "Deploying application to AWS EC2 staging server" 
            } 
        } 
 
        stage("Integration Tests on Staging") { 
            steps { 
                echo "Running integration tests on staging environment using Selenium" 
            } 
        } 
 
        stage("Deploy to Production") { 
            steps { 
                echo "Deploying application to AWS EC2 production server" 
            } 
        } 
    } 
} 
