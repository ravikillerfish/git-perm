pipeline {
    agent any
   // parameters {
    //   gitParameter(branch: '',branchFilter: '.*', defaultValue: '1.22', name: 'TAG', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'GitParameterDefinition')
   // }
    stages {
        stage('git') {
           steps {
              checkout(
  		[
    		  $class: 'GitSCM',
                  extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'git-perm']],
                  branches: [[name: 'refs/heads/${env.BRANCH_NAME}']],
                  userRemoteConfigs: [
                    [
                      url: 'https://github.com/ravikillerfish/git-perm.git',
                      name: 'origin'
                    ]
                 ]           
               ]
             )
           }
        }
        stage('deploy-kube-ansible') {
	   steps {
              ansiblePlaybook extras: '--extra-var "TAG=${TAG}"', installation: 'ansible-kubernetes', inventory: 'hosts', playbook: 'nginx.yaml' 
	   }
	}
    }
}
