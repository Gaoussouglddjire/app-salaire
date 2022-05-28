node{
    stage('Clone git') {
        checkout scm
    }
    stage('Prerequis'){
        sh "apk add ansible sshpass"
        sh "rm -rf /root/.ssh"
        sh "echo \"192.168.56.101 app-salaire.gaoussou.form\" > /etc/hosts"
        sh "ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa"
        sh "sshpass -p 'root' ssh-copy-id -o stricthostkeychecking=no root@192.168.56.102"
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true,
          playbook: 'playbook.yaml',
          inventory: 'hosts.yaml'
      )
    }
}
