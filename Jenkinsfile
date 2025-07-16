pipeline {
  agent any 

  stages {
    stage('Daily Compliance Run') {
      steps{
        echo 'Running a compliance scan with inspec....'
          script{
            def remote = [:]
            remote.name = "controlnode"
            remote.host = "44.246.214.104"
            remote.allowAnyHosts = true

            withCredentials([sshUserPrivateKey(credentialsId: 'ubuntu', keyFileVariable: 'identity', passphraseVariable: '', usernameVariable: 'userName')]) {
                remote.user = userName
                remote.identityFile = identity
                stage("Placeholder Stage...") {
                  sshCommand remote: remote, sudo: true, command: 'echo "add your stuff here....."'
                  sshCommand remote: remote, sudo: true, command: 'echo "some more stuff goes here....."'
              }
                stage("Scan with InSpec") {
                  // sshCommand remote: remote, sudo: true, command: 'inspec exec /root/linux-baseline/'
                  sshCommand remote: remote, command: 'inspec exec linux-baseline/'
              }
            }
          }
       }
    }
  }
}

