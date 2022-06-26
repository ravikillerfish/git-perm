pipeline {
    agent any
    parameters {
       gitParameter(branch: '',branchFilter: '.*', defaultValue: '1.22', name: 'TAG', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'GitParameterDefinition')
    }
    stages {
        stage('git') {
           steps {
              git 'https://github.com/ravikillerfish/Jenkins1.git'
           }
        }
        stage('deploy-kube-ansible') {
	   steps {
              ansiblePlaybook become: true, becomeUser: null, installation: 'ansible-kubernetes', inventory: 'hosts', playbook: 'nginx.yaml', tags: '$TAG'
	   }
	}
    }
}
