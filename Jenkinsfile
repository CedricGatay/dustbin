node('master') {
   stage('checkout') {
       stage('checkout') {
           checkout scm
       }
   }

   docker.image('openjdk:8-jdk').inside('-v /var/cache/gradle:/tmp/gradle-user-home:rw -u 0') {
       try {
           stage('build') {
               sshagent(['cgtestlulu']) {
                   sh "ssh-add -L"
                   sh "GIT_CURL_VERBOSE=1 GIT_TRACE=1 git pull origin master"
               }
           }
       } catch (e) {
           throw e
       }
   }
}
