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
                   // emailext to: 'embeddedinit0@gmail.com',
                    emailext to: 'kocurekmagdalena7@gmail.com',
                    from: 'jenkins@example.com',
                   subject: "Example ",
                   body: "Job succesed",
             //   emailext: 
                  recipientProviders: [developers(), requestor()]
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
