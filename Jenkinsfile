pipeline {
    agent any
    parameters {
    string(name: 'BRANCH_NAME', defaultValue: 'main', description: '') 
    booleanParam(name: 'TF_APPLY', defaultValue: 'false', description: '')
  }
    stages{
      stage('git clone') {
          when{
            expression { BRANCH_NAME == 'main' }
        }
          steps {
                checkout scmGit(git branch: 'main', credentialsId: 'jenkins-github-ssh-key', url: 'git@github.com:gayathrimallisetti118-sys/learn-terraform-provision-eks-cluster.git')
            }
         }
         stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
         }
         stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
         }
        stage('Terraform Plan') {
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
