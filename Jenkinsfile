pipeline {
    agent any

    tools {nodejs "NodeJS"}

    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Cypress run') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    sh 'npm run allure:clear'
                    sh 'npm run cy:run:allure --record --key 8c01844a-96f3-499c-97f6-00f5dbdb8fb6'
                }
            }
        }
        stage('Allure report') {
            steps {
                    sh 'npm run allure:report'
                    sh 'ls'
                    sh 'pwd'
                    allure( 
                        includeProperties: false, 
                        jdk: '', 
                        results: [[path: 'allure-results']])
            }
        }
    }
}