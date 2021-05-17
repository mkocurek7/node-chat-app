pipeline
{
    agent any
  
    tools{nodejs "node"}
   // tools{ docker-build-step } //"docker"}
    
    
    stages
    {
        
       stage('Building') {
           steps{ echo 'Building...'
               //  sh 'git pull origin master'
                // checkout scm
                 
                 sh 'npm install'
             //    sh 'npm run build'
                 
                }
              post{
               success{
                    emailext attachLog: true,
                     to: 'kocurekmagdalena7@gmail.com',
                     subject: "Success Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                    body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
                  recipientProviders: [developers(), requestor()]
                    }
               failure{
                    emailext attachLog: true,
                     to: 'kocurekmagdalena7@gmail.com',
                     subject: "Build failure ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                    body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
                  recipientProviders: [developers(), requestor()]
                     }
               
        } 
       } 
        
        stage('Test') {
            when{ expression{currentBuild.result == 'SUCCESS' || currentBuild.result == null }}
            steps{ echo 'Testing'  
                 sh 'npm run test'}     
             post{
              success{
                 emailext attachLog: true,
                 body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build  ${env.BUILD_NUMBER} ",
                 recipientProviders: [developers(), requestor()],
                 subject: "Success Jenkins Test ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                  to: 'kocurekmagdalena7@gmail.com'        
              }}
            }
         stage('Deploy') {
             steps{echo 'deploy'
                  sh 'docker build --user root -t deploy:latest -f Dockerfile-deploy .'
                 // sh 'docker tag chat:latest kjop118/chat:latest'
                   
                   // sh 'docker save -o ./chatBuild.tar kjop118/chat:latest' //zapisanie obrazu
                    //sh 'docker build -t ubuntu-deploy -f Dockerfile_ubuntu .' 
                  }  
               post{
                 success{
                 emailext attachLog: true,
                 body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build  ${env.BUILD_NUMBER} ",
                 recipientProviders: [developers(), requestor()],
                 subject: "Success Jenkins Deploy ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                  to: 'kocurekmagdalena7@gmail.com'        
              }}
            }
         
           
           
           
     }  
  }
