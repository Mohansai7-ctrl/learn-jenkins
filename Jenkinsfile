pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo "This is from Build"
            }
        }

        stage("Test") {
            steps {
                echo "This is from Test"
            }
        }

        stage("Deploy") {
            steps {
                echo "This is from Deploy"
            }
        }
    }

    post {
        always {
            echo "This condition runs always irrespective of above pipeline success or not"
        }

        success {
            echo "This condition runs only above pipeline success"
        }

        failure {
            echo "This condition runs only above pipeline failure"
        }
    }
}