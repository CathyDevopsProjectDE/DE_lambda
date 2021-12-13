pipeline {
    agent {
        docker {  image 'zenika/terraform-aws-cli:latest' }
    }
    // parameters {
    //     string(name: 'environment', defaultValue: 'default', description: 'Workspace/environment file to use for deployment')
    //     string(name: 'version', defaultValue: '', description: 'Version variable to pass to Terraform')
    //     booleanParam(name: 'autoApprove', defaultValue: false, description: 'Automatically run apply after generating plan?')
    // }
    // environment {
    //     AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
    //     AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    //     TF_IN_AUTOMATION      = '1'
    // }
    stages {
        // stage('git checkout'){
        //     steps{
        //             sh 'ls -a'
        //             // git branch: 'AW-211.212/Send-company-invitation-email', credentialsId: '9d2efa7d-31f1-44d0-a5b4-3e0926e05388', url: 'https://github.com/asyncworking/aw-lambda-sendemail.git'                   
        //     }
        // }
        
        stage('preparation before deloy'){
            steps{
                  withAWS(credentials: '8058ad1c-fdf5-4ae4-b62d-a0127bcd6006', region:'ap-southeast-2'){ 
                      sh 'ls -a'
                      sh 'cat .env'
                      // sh 'rm -rf aws-ses-local'
                      sh 'apt-get update'
                      sh 'apt -y install curl'
                      sh 'curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh'
                      sh 'bash nodesource_setup.sh'
                      sh 'apt install nodejs'
                      sh 'npm install'
                      sh 'mkdir -p ~/.docker/cli-plugins/'
                      sh 'curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                      sh 'chmod +x /usr/local/bin/docker-compose'
                      sh 'docker-compose version'
                      sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
                      sh 'sh get-docker.sh'
                      sh 'npm i python'
                      sh 'apt-get -y install python3-pip'
                      sh 'pip install aws'
                    //   sh 'pip install awscli-local'
                    //   sh 'npm install aws-ses-local -g'
                    //   sh 'npm install jest'
                    //   sh 'chmod a+x ./end_to_end_test/setup-localtest.sh'
                  }
            }
        }      
                  
                 
    //     stage('zip files') {
    //         steps{
    //             sh 'apt-get update'
    //             sh 'apt-get -y install zip'
    //             sh 'zip  lambda-jk-tf-test7.zip src/index.js node_modules/dotenv src/helpers/templateHelper.js src/helpers/emailHelper.js'
    //             sh 'ls -a'
    //             sh 'pwd lambda-jk-tf-test7.zip'
    //             withAWS(credentials: '8058ad1c-fdf5-4ae4-b62d-a0127bcd6006', region:'ap-southeast-2'){ 
    //             sh 'aws s3 cp lambda-jk-tf-test7.zip s3://jk-tf-s3-test7/lambda-functions/lambda-jk-tf-test7.zip'
    //             }
    //               }
    //     }
        
    //     stage('Terraform Init') {
    //         steps{
    //             sh 'terraform init'
    //               }
    //     }
    //     stage('Terraform plan') {
    //         steps{
    //             withAWS(credentials: '8058ad1c-fdf5-4ae4-b62d-a0127bcd6006', region:'ap-southeast-2'){  
    //                 sh 'terraform plan -out=tfplan -input=false'
    //         }
    //     }
    // }
    //     stage('Terraform apply'){
    //         steps{
    //             withAWS(credentials: '8058ad1c-fdf5-4ae4-b62d-a0127bcd6006', region:'ap-southeast-2'){
    //                 sh "terraform apply -input=false tfplan"
    //             }
    //         }            
    //     }
    }
}