pipeline {

    agent {

        node { label "maven" }

    }
    
    environment { QUAY = credentials('QUAY_USER') }



    stages {

        stage("Test") {

            steps {

                sh "./mvnw verify"

            }

        }

       	stage("Build & Push Image") {

            steps {

                
                sh '''

                    ./mvnw package -DskipTests \

                    -Dquarkus.jib.base-jvm-image=https://quay.io/organization/redhattraining/do400-java-alpine-openjdk11-jre \

                    -Dquarkus.container-image.build=true \

                    -Dquarkus.container-image.registry=quay.io \

                    -Dquarkus.container-image.group=$QUAY_USR \

                    -Dquarkus.container-image.name=do400-deploying-lab \

                    -Dquarkus.container-image.username=$QUAY_USR \

                    -Dquarkus.container-image.password="$QUAY_PSW" \

                    -Dquarkus.container-image.tag=build-${BUILD_NUMBER} \

                    -Dquarkus.container-image.additional-tags=latest \

                    -Dquarkus.container-image.push=true

                '''

            }

        }

    }

}
