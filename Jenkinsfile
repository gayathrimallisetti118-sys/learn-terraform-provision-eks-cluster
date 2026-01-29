pipeline {
    agent any
    parameters {
    booleanParam(name: 'TF_INIT', defaultValue: 'true', description: '')
    booleanParam(name: 'TF_VALIDATE', defaultValue: 'true', description: '')
    booleanParam(name: 'TF_PLAN', defaultValue: 'true', description: '')
    booleanParam(name: 'TF_APPLY', defaultValue: 'false', description: '')
  }
    stages{
      stage('git clone') {
          steps {
                git branch: 'main',
                url: 'https://github.com/gayathrimallisetti118-sys/learn-terraform-provision-eks-cluster.git'
            }
         }
         stage('Terraform Init') { 
             when {
                expression { params.TF_INIT }
        }
            steps {
                sh 'terraform init'
            }
         }
         stage('Terraform Validate') {
             when {
                expression { params.TF_VALIDATE  }
        }
            steps {
                sh 'terraform validate'
            }
         }
        stage('Terraform Plan') { 
            when {
                expression { params.TF_PLAN  }
        }
            steps {
               sh 'terraform plan'
           }
        } 
        stage('Terraform Apply'){
         when {
                expression { params.TF_APPLY }
        }
        steps{
          sh 'terraform apply -auto-approve'
        }
    }
 }
}





