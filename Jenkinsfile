pipeline {

 agent { label 'jobdsl' }


 stages {

 stage(‘checkout’) {

 steps {

 git branch: 'master',

    url: 'ssh://jenkins@gerrit.1dc.com:29418/EMEA/CIO/AWS/AWS-POC'

 

 }

 }

 stage('Set Terraform path') {

 steps {

 script {

 def tfHome = '/apps/jenkins/tools/terraform-0.11.14'

 env.PATH = "${tfHome}:${env.PATH}"

 }

 sh 'terraform --version'

 

 }

 }

 

 stage('Provision infrastructure') {

 

 steps {

 dir('simple')

 {

 sh 'terraform init'

 sh 'terraform plan -out=plan'

 // sh ‘terraform destroy -auto-approve’

 sh 'terraform apply plan'

 }
 
 }

 }

 }

}
