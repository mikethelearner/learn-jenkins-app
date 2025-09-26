pipeline{

    agent any

    stages{

          stage('Build'){
              agent{
                  docker{
                      image 'node:14-alpine'
                      reuseNode true
                  }
              }

              steps{

                   sh '''

                       ls -la
                       npm --version
                       npm --version
                       npm ci
                       npm run build

                   '''
                  
              }
          }


    }



    
}