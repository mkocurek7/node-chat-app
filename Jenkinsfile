pipeline
{
    agent any
    
    stages
    {
         stage('Declarative: Tool Install') {
           steps{ echo 'here should be tools.'
                 tools{nodejs "nodejs"}
                } 
        }
      
       stage('Build') {
           steps{ echo 'Building...'
                 echo 'sciezka'
                echo '$PATH'} 
           post{
               success{
                    emailext attachLog: true,
                     to: 'kocurekmagdalena7@gmail.com',
                     subject: "Build successful ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
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
            //when{ expression{currentBuild.result == 'SUCCESS'}}
            steps{ echo 'Testing'    }     
             post{
              success{
                 emailext attachLog: true,
                 body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ",
                 recipientProviders: [developers(), requestor()],
                 subject: "Success Jenkins Test ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                  to: 'kocurekmagdalena7@gmail.com'        
              }}
            }
         stage('Deploy') {
             steps{echo 'deploy' }  
               post{
                 success{
                 emailext attachLog: true,
                 body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ",
                 recipientProviders: [developers(), requestor()],
                 subject: "Success Jenkins Deploy ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                  to: 'kocurekmagdalena7@gmail.com'        
              }}
            }
         
     }  
  }
