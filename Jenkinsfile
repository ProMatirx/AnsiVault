#!groovy
import groovy.transform.Field

node {

   stage('Git Check out')
   {
   sh "rm -rf /root/Newone"
   
		sh " echo $BUILD_NUMBER "
		sh " echo $WORKSPACE "
		sh " echo $JOB_NAME "
   
		sh ' echo $? '
   
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/MuraliKarre/Vault.git']]])
   
		sh " ansible-playbook $WORKSPACE/1.playbook.yml --tags git --vault-password-file ~/.pass "
		sh ' echo $? '
		sh "ls -la"
   }
   stage('Docker login')
   {
       echo "Docker Login"
	   
       sh " ansible-playbook $WORKSPACE/1.playbook.yml --tags dok --vault-password-file ~/.pass "
	   
	   sh ' echo $? '
   
   
   }
  

}

