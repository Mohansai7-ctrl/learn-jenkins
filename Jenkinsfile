// Make sure to install plugins from Manage Jenkins are 1) pipeline stage view and 2)pipeline utility steps

pipeline {

    agent {
        label 'AGENT-1'   //So that you schedule the build from jenkins ui which is on Master, but as agent is provided it runs in the AGEN-1
    }

    options {
        disableConcurrentBuilds() //It will disable to allow concurrent builds means multiple builds to run at same time
        retry(1)  //If build got failed then only it will retry for 1 more time
        timeout(time: '10', unit: 'SECONDS')  //it Will wait for 10 seconds, within that if build didnt get run then it will throw timeout error
    }

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
            deleteDir()    //It will delete the created directory after or once the pipeline is triggered or execured successfully
        }
        

        success {
            echo "This condition runs only above pipeline success"
        }

        failure {
            echo "This condition runs only above pipeline failure"
        }
    }
}