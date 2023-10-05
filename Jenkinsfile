pipeline{

        agent any

        stages{

            stage('Build docker images on Jenkins'){

                steps{

                    sh '''

                    docker build -t selvasuba/duo-nginx:latest ./nginx

                    docker build -t selvasuba/duo-flask:latest .

                    '''

                }

            }

            stage('Push images to Docker Hub'){

                steps{

                    sh '''

                    docker push selvasuba/duo-nginx:latest

                    docker push selvasuba/duo-flask:latest

                    '''

                }

            }

            stage('Run a rollout restart'){

                steps{

                    sh '''

                    kubectl apply -f .

                    kubectl rollout restart deployment flask-deployment

                    '''

                }