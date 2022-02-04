pipeline {
    agent any
    tools{
        terraform 'terraform'
    }
    
    stages {
        
        stage ('Terraform init'){
            steps {
                sh 'terraform init -input=false'    
            }
            
        }
        
        stage ('Terraform validate'){
            steps {
                sh 'terraform validate'    
            }
            
        }
        
        stage ('Terraform plan'){
            steps {
                sh 'terraform plan -out=tfplan -input=false'
            }
            
        }
        stage ('Email Notification'){
            mail bcc: '', body: '''$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

            Check console output at $BUILD_URL to view the results.''', cc: '', from: '', replyTo: '', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'ameydevarshi1@gmail.com'
            
        }
  }
}
