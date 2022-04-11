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
                sh "docker run --name my-postgres -e POSTGRES_PASSWORD=secret -p 5432:5432 -d postgres"
            }
        }

        stage("Run backend"){
            steps{
                sh "docker run -p 80:8080  -e DB_HOST=$(docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-postgres) --name backend_cnt -d ${ARTIFACT_ID}:latest"
            }
        }
        // stage('Run UI Tests') {
        //     steps {
        //         sh "docker run -p 3030:3030 ${env.ARTIFACT_ID} npm test"
        //     }
        // }

    }  


}