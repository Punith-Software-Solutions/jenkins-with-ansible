pipeline {
  agent { 
  label 'ansible'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
       git credentialsId: '5b9436f3-1052-49e0-b090-8060667f8fe6', url: 'https://github.com/Punith-Software-Solutions/jenkins-with-ansible.git'
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
