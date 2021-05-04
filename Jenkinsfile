pipeline{
    agent any
    tools{nodejs "NodeJS"}
    stages {
        stage('Test'){
          steps{
            echo 'Testing'
            sh 'npm install'
            sh 'npm run test'
            }        
        }
    }

    post{
        success{
            emailext attachLog: true,
            body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NAME}",
            recipientProviders: [developers(), requestor()],
            subject: "Success Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
            to: 'kocurekmagdalena7@gmail.com'        
        }
        failure{
            emailext attachLog: true,
            body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NAME}",
            recipientProviders: [developers(), requestor()],
            subject: "Failure Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
            to: 'kocurekmagdalena7@gmail.com'        
        }
        
    }

}
