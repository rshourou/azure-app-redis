pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

      stage ('Push Container'){
         steps {
            echo "Workspace : $WORKSPACE"
            dir ("azure-vote") {
               script {
                  docker.withRegistery ('https://index.docker.io/v1', 'DockerHub')
                  def image = docker.build ('rshourou/jenkin_multipipeline:latest')
                  image.push()
               }
            }
         }

      }
  
      
   }
}
