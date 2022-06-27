pipeline {
    agent any
   // parameters {
    //   gitParameter(branch: '',branchFilter: '.*', defaultValue: '1.22', name: 'TAG', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'GitParameterDefinition')
   // }
    stages {
        stage('git') {
           steps {
              git branch: '$branch', url: 'https://github.com/ravikillerfish/git-perm.git''
           }
        }
        stage('deploy-kube-ansible') {
	   steps {
              ansiblePlaybook extras: '--extra-var "TAG=1.22"', installation: 'ansible-kubernetes', inventory: 'hosts', playbook: 'nginx.yaml' 
	   }
	}
    }
}
