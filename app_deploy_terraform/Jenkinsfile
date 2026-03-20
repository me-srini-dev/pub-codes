pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-key')
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-repo/sample-app.git'
            }
        }

        // 👇 ADD YOUR NEW STAGE HERE
        stage('Terraform') {
            steps {
                dir('app_deploy_terraform/terraform') {
                    sh '''
                        terraform --version
                        terraform init
                        terraform plan
                        terraform apply -auto-approve
                    '''
                }
            }
        }

    }
}