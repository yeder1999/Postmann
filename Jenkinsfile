pipeline {
    agent {
        docker {
            image 'postman/newman:latest'
            args '-u root --entrypoint='
        }
    }


    stages {

        stage('Installer Allure') {
            steps {
                sh 'npm install -g newman-reporter-allure'
            }
        }

        stage('Lancer les tests') {
            when {
                expression {
                    params.CICD
                }
            }

            steps {
                sh '''
                    newman run CICD.json \
                    -e preprod.json \
                    --reporters cli,allure \
                    --reporter-allure-resultsDir output/allure-results
                '''
            }
        }
    }
}