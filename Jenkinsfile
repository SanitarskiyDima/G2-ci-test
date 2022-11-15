pipeline {
    agent any

    tools {nodejs "NodeJS"}

    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Cypress run auth') {
            steps {
                sh 'npm run allure:clear'
                sh 'npm run cy:run:allure --spec "cypress/e2e/authorization.cy.js"'
            }
            steps {
                sh 'npm run allure:clear'
                sh 'npm run cy:run:allure --spec "cypress/e2e/order.cy.js"'
            }
        }
        stage('Allure report') {
            steps {
                sh 'npm run allure:generate'
            }
        }
    }
}