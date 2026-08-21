pipeline {
    agent {
        docker {
            image 'postman/newman:latest'
            args '-u root --entrypoint='
        }
    }

    parameters {
        booleanParam(
            name: 'CICD',
            defaultValue: true,
            description: 'Lancer la collection CICD.json'
        )
    }

    stages {
        stage('Lancer les tests') {
            steps {
                sh 'newman run CICD.json -e preprod.json'
            }
        }
    }
}