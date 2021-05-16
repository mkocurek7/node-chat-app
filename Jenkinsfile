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
               always{ 
                emailext: 
                   body: "build",
                    recipientProviders: [developers(), requestor()],
                    subject: "Success Jenkins ",
                     to: 'kocurekmagdalena7@gmail.com'  
               }
           }
        }
        stage('Test')
        {
          steps{
            echo 'Testing'
           
               }        
         }
         stage('Deploy')
        {
          steps{
            echo 'Testing'
           
               }        
         }
         stage('Declarative: Post Actions') {
           steps{ echo 'here should be tools.' } 
        }
     }  
  }
