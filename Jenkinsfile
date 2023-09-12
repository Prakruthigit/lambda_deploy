pipeline {
    agent any
    environment {

        DEV_LAMBDA_FUNCTION_NAME = 'dev_function'
        QA_LAMBDA_FUNCTION_NAME = 'qa_function'
        STAGING_LAMBDA_FUNCTION_NAME = 'staging_function'
        PRODUCTION_LAMBDA_FUNCTION_NAME = 'master_function'

    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

                stage('Build') {
            steps {
                 sh "zip my_deployment.zip lambda_function.py"
            }
        }

        stage('Deploy to Dev Lambda') {
            when {
                branch 'dev'
            }
			steps {
                                sh "mv my_deployment.zip ${BRANCH_NAME}_deployment.zip"
                                withCredentials([string(credentialsId: 'access_key', variable: 'ACCESS_KEY'), string(credentialsId: 'secret_key', variable: 'SECRET_KEY')]) {
                                        sh "aws lambda update-function-code --function-name $DEV_LAMBDA_FUNCTION_NAME --zip-file fileb://./${BRANCH_NAME}_deployment.zip"

                                 }

            }

        }
                stage('Deploy to QA Lambda') {
            when {
                branch 'qa'
            }
            steps {
                                sh "mv my_deployment.zip ${BRANCH_NAME}_deployment.zip"
                                withCredentials([string(credentialsId: 'access_key', variable: 'ACCESS_KEY'), string(credentialsId: 'secret_key', variable: 'SECRET_KEY')]) {
                                        sh "aws lambda update-function-code --function-name $QA_LAMBDA_FUNCTION_NAME --zip-file fileb://./${BRANCH_NAME}_deployment.zip"

                                 }

            }

        }
                stage('Deploy to STAGING Lambda') {
            when {
                branch 'staging'
            }
            steps {
                                sh "mv my_deployment.zip ${BRANCH_NAME}_deployment.zip"
                                withCredentials([string(credentialsId: 'access_key', variable: 'ACCESS_KEY'), string(credentialsId: 'secret_key', variable: 'SECRET_KEY')]) {
                                        sh "aws lambda update-function-code --function-name $STAGING_LAMBDA_FUNCTION_NAME --zip-file fileb://./${BRANCH_NAME}_deployment.zip"

                                 }

            }

        }
                stage('Deploy to PRODUCTION Lambda') {
            when {
                branch 'dev'
            }
            steps {
                                sh "mv my_deployment.zip ${BRANCH_NAME}_deployment.zip"
                                withCredentials([string(credentialsId: 'access_key', variable: 'ACCESS_KEY'), string(credentialsId: 'secret_key', variable: 'SECRET_KEY')]) {
                                        sh "aws lambda update-function-code --function-name $PRODUCTION_LAMBDA_FUNCTION_NAME --zip-file fileb://./${BRANCH_NAME}_deployment.zip"

                                 }

            }

        }
        }
}


