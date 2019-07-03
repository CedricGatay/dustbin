node('master') {
   stage('checkout') {
       stage('checkout') {
           checkout scm
       }
   }

   docker.image('openjdk:8-jdk').inside('-v /var/cache/gradle:/tmp/gradle-user-home:rw') {
       try {
           stage('build') {
               sshagent(['cgtestlulu']) {
                   sh "git pull"
               }
           }
       } catch (e) {
           throw e
       }
   }
}
