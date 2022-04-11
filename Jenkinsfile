pipeline{
      agent { label 'slave1' }
      stages{
      stage('check out'){
                  steps{
                  sh "rm -rf hello-world-war"
                  sh "git clone https://github.com/fgoswami/hello-world-war.git"
                  }
                  }
      stage('build'){
      steps{
      sh "pwd"
      sh "ls"
      sh "cd hello-world-war"
      sh "docker build -t riya9578/riyanewrepo:1.0 ."
      }
      }
       stage('publish'){
                  steps{
                        sh "docker login -u riya9578 -p Falguni@123"
                        sh "docker push riya9578/riyanewrepo:1.0"
                  }
            }
            stage('deploy'){
                  agent { label 'slave2' }
                  steps{
                        sh "docker login -u riya9578 -p Falguni@123"
                        sh "docker pull riya9578/riyanewrepo:1.0"
                        sh "docker rm -f trail1"
                        sh "docker run -d -p 8085:8080 --name trail1 riya9578/riyanewrepo:1.0"
                  }
            }
      }
      }
