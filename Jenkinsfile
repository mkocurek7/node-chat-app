pipeline{
    agent any
    tools{nodejs "NodeJS"}
    stages {
        stage('Build') {
            steps{
                echo 'Building'
                sh 'npm install'
                sh 'npm run build'    
            }
        }
        stage('Test'){
          steps{
            echo 'Testing'
            sh 'npm run test'
            }        
        }
    }

    post{
        success{
            emailtext attachLog: true,
            body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NAME}",
            recipientProviders: [developers(), requestor()],
            subject: "Success Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
            to: 'kocurekmagdalena7@gmail.com'        
        }
        failure{
            emailtext attachLog: true,
            body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NAME}",
            recipientProviders: [developers(), requestor()],
            subject: "Failure Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
            to: 'kocurekmagdalena7@gmail.com'        
        }
        
    }

}
