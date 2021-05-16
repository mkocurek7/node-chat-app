pipeline
{
    agent any
    tools {nodejs "NodeJS"}
    stages
    {
         stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test')
        {
          steps{
            echo 'Testing'
            sh 'npm test'
               }        
         }
     }  
  }
