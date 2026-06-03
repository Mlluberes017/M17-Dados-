pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "mlluberes/m17-dados"
        DOCKER_TAG = "latest"
        CONTAINER_NAME = "m17-dados-test"
    }

    stages {
        stage('Limpiar workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Clonar repositorio') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Mlluberes017/M17-Dados-.git'
            }
        }

        stage('Construir imagen Docker') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:$DOCKER_TAG .'
            }
        }

        stage('Ejecutar contenedor de prueba') {
            steps {
                sh '''
                    docker rm -f $CONTAINER_NAME || true
                    docker run --name $CONTAINER_NAME $DOCKER_IMAGE:$DOCKER_TAG
                '''
            }
        }

        stage('Eliminar contenedor de prueba') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Subir imagen a DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKERHUB_USER',
                    passwordVariable: 'DOCKERHUB_PASS'
                )]) {
                    sh '''
                        echo "$DOCKERHUB_PASS" | docker login -u "$DOCKERHUB_USER" --password-stdin
                        docker push $DOCKER_IMAGE:$DOCKER_TAG
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente. Imagen construida, probada y subida a DockerHub.'
        }

        failure {
            echo 'El pipeline ha fallado. Revisar los logs de Jenkins para identificar el error.'
        }

        always {
            sh 'docker rm -f $CONTAINER_NAME || true'
        }
    }
}
