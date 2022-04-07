pipeline {
    agent any

    options {
        timeout(time: 3, unit: 'MINUTES')
    }

    environment {
        ARTIFACT_ID = "juan2203/backendpraxis2022"
    }

    stages {
        stage("Run database"){
            steps{
                sh "docker network create praxis-net"
                sh "docker run --net praxis-net -d --name my-postgres -e POSTGRES_PASSWORD=secret -p 5433:5432 -d postgres"
                sh "docker run --net praxis-net -d ${env.ARTIFACT_ID}:latest -p 80:8080"
            }
        }

        // stage('Run UI Tests') {
        //     steps {
        //         sh "docker run -p 3030:3030 ${env.ARTIFACT_ID} npm test"
        //     }
        // }

    }  


}