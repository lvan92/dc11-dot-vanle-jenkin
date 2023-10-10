pipeline{
    agent any
    triggers {
        GenericTrigger(
            genericVariables: [[key: 'ref', value: '$.ref']],
            token: 'abc123',
            causeString: 'Triggered on $ref',
            regexpFilterExpression: '',
            regexpFilterText: '',
            printContributedVariables: true,
            printPostContent: true
        )
    }
    stages{
        stage("Clone"){
            steps{
                git branch: 'prod', url: "https://github.com/lvan92/dc11_dot_vanle_terraform", credentialsId: 'ee7270cf-02cf-41aa-b1e0-bb4dd14636bc'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
                echo '[Debug] Running terraform init successfully~'
            }
        }
        stage('Terraform Validate') {
            steps {
                sh 'terraform fmt'
                sh 'terraform validate'
            }
        }
    }
    post{
        success{
           echo "Success"
        }

        failure{
            echo "Failure"
        }
    }
}