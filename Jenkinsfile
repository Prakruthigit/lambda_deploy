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

        stage('echo branchname'){
            steps {
                echo ${BRANCH_NAME}
            }
        }
    }
}
