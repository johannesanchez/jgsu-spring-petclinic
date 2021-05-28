pipeline {
    agent any
    triggers { pollSCM('*/2 * * * *') }
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
                        git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'dev'
                        sh "echo Parallel on devBranch; sleep 5s; echo finished phase p2 devBranch"
                        },
                    failFast: true //|false
                )
            }
        }
    }
}
        //Added this lines to create dev branch on remote
        // stage('Checkout'){
        //     steps {
        //         git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
        //     }
        // }