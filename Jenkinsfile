pipeline {
    agent any
    triggers { pollSCM('*/5 * * * *') }
    stages {
        stage('Checkout'){
            steps {
                parallel masterBranch: {
                git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
                }, devBranch: {
                git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'dev'
                },
                failFast: true //|false
                }
            }

        // stage('Checkout'){
        //     steps {
        //         git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
        //     }
        // }
    }
}
