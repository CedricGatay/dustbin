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
                  sh "mkdir ~/.ssh"
                  sh "ssh-keyscan -t rsa github.com > ~/.ssh/known_hosts"
                  sh "ssh-add -L"
                  sh "GIT_CURL_VERBOSE=1 GIT_TRACE=1 git pull origin master"
                  sh "echo \$(date) >> date"
                  sh "git add date"
                  sh "git config --global user.email 'you@example.com'"
                  sh "git config --global user.name 'Your Name'"
                  sh "git commit -m'committing'"
                  sh "git push"
               }
           }
       } catch (e) {
           throw e
       }
   }
}
