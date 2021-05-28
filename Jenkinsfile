pipeline {
    agent any
    triggers { pollSCM('*/2 * * * *') }
    environment {
        BRANCH_NAME = "${env.BRANCH_NAME}"
    }
    stages {
        stage('Checkout'){
            steps {
                parallel(
                    masterBranch: {
                        echo "This is branch Master"
                        git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
                        sh "echo Parallel on masterBranch; sleep 5s; echo finished phase p1 masterBranch"
                        },
                    devBranch: {
                        echo "This is branch dev"
                        // git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'dev'
                        sh "echo Parallel on devBranch; sleep 30s; echo finished phase p2 devBranch"
                        },
                    failFast: true //|false
                )
                // sh "echo run this after both phases complete"
            }
        }
        stage('Deploy approval'){
            steps {
                echo "This is the message for Deploy Approval"
                input "Do you want to proceed for prod deployment?"
                echo "Deploying ..."
            }
        }
        stage('Post-Deploy'){
            steps {
                echo "This is the message for post-Deploy"
            }
        }
    }

    post {
        always {
            echo "General Build successful"
        }
        success {
            echo "Successfully !!!"
        }
    }

    options {
        timeout(time: 60, unit: 'MINUTES')
    }
}
        //Added this lines to create dev branch on remote
        // stage('Checkout'){
        //     steps {
        //         git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
        //     }
        // }