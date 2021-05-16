pipeline
{
    agent any
    stages
    {
         stage('Declarative: Tool Install') {
           steps{ echo 'here should be tools.' } 
        }
      
       stage('Build') {
           steps{ echo 'Building...' } 
           post{
               success{
              // always{ 
                  
                    emailext attachLog: true,
                     to: 'kocurekmagdalena7@gmail.com',
                   // from: 'jenkins@example.com',
                        subject: "Success Jenkins Test ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                    body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NAME}",
             //   emailext: 
                  recipientProviders: [developers(), requestor()]
               }
           }
        }
        stage('Test') { steps{ echo 'Testing'    }         }
         stage('Deploy') {steps{echo 'deploy' }         }
         
     }  
  }
