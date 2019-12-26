pipeline {
    agent any
     
    stages {
        stage ('checkout'){
            steps {
                git branch: 'master', url: 'https://github.com/ishaqmdgcp/test01.git'
            }
        }
      

		stage('Set Terraform path') {
            steps {
                script {
                    def tfHome = tool name: 'Terraform'
                    env.PATH = "${tfHome}:${env.PATH}"
                }
                sh 'terraform --version'
               
               
            }
        }
        
         stage('Provision infrastructure') {
            steps {
                sh 'terraform init'
                sh 'terraform plan'
                sh 'terraform destroy -auto-approve'
                             
             
            }
        }
        
        
      
      
    }
}
