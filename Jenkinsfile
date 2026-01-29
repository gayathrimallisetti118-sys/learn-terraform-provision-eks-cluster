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
                checkout scmGit(git branch: 'main', credentialsId: 'jenkins-github-ssh-key', url: 'git@github.com:gayathrimallisetti118-sys/learn-terraform-provision-eks-cluster.git')
            }
         }
         stage('Terraform Init') { 
             when {
                expression { TF_INIT == 'true' }
        }
            steps {
                sh 'terraform init'
            }
         }
         stage('Terraform Validate') {
             when {
                expression { TF_VALIDATE == 'true' }
        }
            steps {
                sh 'terraform validate'
            }
         }
        stage('Terraform Plan') { 
            when {
                expression { TF_PLAN == 'true' }
        }
            steps {
               sh 'terraform plan'
           }
        } 
        stage('Terraform Apply'){
         when {
                expression { TF_APPLY == 'false' }
        }
        steps{
          sh 'terraform apply -auto-approve'
        }
    }
 }

