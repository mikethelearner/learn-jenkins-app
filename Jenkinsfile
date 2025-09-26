pipeline{

    agent any

    stages{

          stage('Build'){
              agent{
                  docker{
                      image 'node:16-alpine'
                      reuseNode true
                  }
              }
              
                  
              environment {
                   NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
                   HOME = "${WORKSPACE}"
              }

              steps{

                   sh '''

                       ls -la
                       npm --version
                       npm --version
                       npm ci
                       npm run build
                       ls -la

                   '''
                  
              }
          }

          stage('Test'){
            agent{
                  docker{
                      image 'node:16-alpine'
                      reuseNode true
                  }
              }
                
            steps{

               sh 'test -f build/index.html'
               sh 'npm test'

            }    
              

          }
          
        
    }   

    post {
         always{

            junit 'test-results/junit.xml'   

         }

    }
}