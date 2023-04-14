pipeline {
    agent any

    stages {
    //    stage('checkout'){
      //      steps {
        //        checkout([$class: 'GitSCM', branches: [[name: '*/main']],userRemoteConfigs: [[url: 'https://github.com/satyasaranu/terraform_ec2.git']]])
          //  }
        //} 

        stage('init') {
            steps {
                sh 'terraform init'
            }
        }
        
        stage('plan') {
            steps {
                
                withCredentials([[
          $class: 'AmazonWebServicesCredentialsBinding',
          credentialsId: "satya_aws_keys",
          accessKeyVariable: 'AWS_ACCESS_KEY_ID',
          secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
        ]]) {
                sh 'terraform plan'
                }
            }
        }
    }
}
