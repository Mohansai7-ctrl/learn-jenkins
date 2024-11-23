// Make sure to install plugins from Manage Jenkins are 1) pipeline stage view and 2)pipeline utility steps

pipeline {

    agent {
        label 'AGENT-1'   //So that you schedule the build from jenkins ui which is on Master, but as agent is provided it runs in the AGEN-1
    }

    options {
        disableConcurrentBuilds() //It will disable to allow concurrent builds means multiple builds to run at same time
        retry(1)  //If build got failed then only it will retry for 1 more time
        timeout(time: 10, unit: 'MINUTES')  //it Will wait for 10 seconds, within that if build didnt get run then it will throw timeout error, these retry, timout can also be used within stage as these are stage options as well.
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Mohan', description: 'To whom should I say hell to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Please Enter the description about you')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Please select anyone')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Please enter the password')
    }

    stages {
        stage("Build") {
            steps {
                echo "This is from Build"
                //sh 'sleep 10' //after this stage, will wait for 10 seconds and then go to next stage
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
                //error 'pipeline failed'  //if error is included, then it will show as error only though it was true
            }
        }

        stage("Print Params") {
            steps {
                echo "Name is: ${params.PERSON}"
                echo "Biography is: ${params.BIOGRAPHY}"
                echo "Toggle is: ${params.TOGGLE}"
                echo "choice is: ${params.CHOICE}"
                echo "password is: ${PASSWORD}"
            }
        }

        stage("Approval") {
            input {
                message "Should we continue?"
                ok "Yes, we can continue!"
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue 'Mr.Mohan', description 'to whom should I say hell to?')
                }
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