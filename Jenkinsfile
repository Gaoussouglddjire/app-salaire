node{
    stage('Clone git') {
        checkout scm
    }
    stage('Prerequis'){
        sh "apk add ansible sshpass"
        sh "rm -rf /root/.ssh"
        sh "echo \"192.168.56.102 app-salaire.moham.form\" > /etc/hosts"
        sh ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa
        sh sshpass -p 'centos' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.gaoussou.form
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true,
          playbook: 'playbook.yaml',
          inventory: 'hosts.yaml'
      )
    }
}
