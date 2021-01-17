pipeline {
    agent any
    parameters{
        //string(name: 'VERSION', defaultValue: '', description: 'version to build')
        //choice(name: 'VERSION', choices: ['1.0', '1.1', '1.2'], description: 'versions to choose from')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    /*tools {
        gradle 'Gradle'
        jdk
    }*/
    stages {
        stage('BUILD') {
            /*when {
                expression {
                    BRANCH_NAME == 'master' && CODE_CHANGES == true
                }
            }*/
            steps {
                echo '================= BUILD TEST PROJECT ================='
                echo "building version ${params.VERSION} : gradlew clean build"
                sh './gradlew clean build -x test'
            }
        }
        stage('TEST') {
            when {
                expression {
                    //BRANCH_NAME == 'master' || BRANCH_NAME == 'dev' // http://localhost:8080/env-vars.html/
                    params.executeTests
                }
            }
            steps {
                 echo '================= RUN TESTS ========================='
                 echo 'executing: gradlew test'
                 sh './gradlew test'
            }
        }
    }

    /*post {
        always{
        // send an e-mail
         }

         success{
         }

         failure{
         }
    }*/
}