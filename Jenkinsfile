pipeline{
    agent any 
    environment {
        PATH = "${PATH}:${getTerraformPath()}"
    }

    stages{
        stage('terraform init and apply - dev'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new dev'                
                sh "terraform init -reconfigure"
                sh "terraform plan"
                // sh "terraform apply -var-file=dev.tfvars -auto-approve"
                //sh "terraform destroy"
            }            
        }
    }
}

def getTerraformPath(){
    def tfHome=tool name: 'terraform-12', type: 'terraform'
    return tfHome
}