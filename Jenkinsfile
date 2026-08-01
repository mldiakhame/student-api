pipeline {
    agent any
    tools {
        maven 'Maven-3.9'
        jdk   'JDK-17'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Build #${env.BUILD_NUMBER} | Branche : ${env.BRANCH_NAME}"
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }
        stage('Lint') {
                    steps {
                        bat 'mvn checkstyle:check'
                    }
                }
        stage('Tests Unitaires') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Couverture') {
            steps {
                bat 'mvn verify'
            }
            post {
                always {
                    jacoco(
                        execPattern:   'target/*.exec',
                        classPattern:  'target/classes',
                        sourcePattern: 'src/main/java'
                    )
                }
            }
        }
        stage('Archivage') {
            steps {
                archiveArtifacts artifacts:    'target/*.jar',
                                 fingerprint: true
            }
        }
    }
    post {
        success { echo 'Pipeline reussi avec succes !'         }
        failure { echo 'Pipeline echoue -- consultez les logs.' }
    }
}
