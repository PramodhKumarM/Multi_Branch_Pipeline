pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MyMaven') {
                    sh 'mvn clean install'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MyMaven') {
                    sh 'mvn test'
                }
            }
        }

        stage('Generate HTML report') {
            steps {
                cucumber buildStatus: "UNSTABLE",
                        fileIncludePattern: '**/cucumber.json',
                        jsonReportDirectory: 'target'
            }

        }
    }
}
