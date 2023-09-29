pipeline{
    agent any
    stages{
        stage("Clone"){
            steps{
                git branch: 'prod', url: "https://github.com/lvan92/dc11_dot_vanle_terraform", credentialsId: 'ee7270cf-02cf-41aa-b1e0-bb4dd14636bc'
            }
        }
    }
    post{
        success{
            mail bcc: '', body: '${BUILD_NUMBER}-${BUILD_ID}-${BUILD_URL}-${NODE_NAME}-${JOB_NAME}', cc: 'manager@yopmail.com, tmquoc@tma.com.vn', from: '', replyTo: '', subject: '${BUILD_TAG}'
        }

        failure{
            mail bcc: '', body: '${BUILD_NUMBER}-${BUILD_ID}-${BUILD_URL}-${NODE_NAME}-${JOB_NAME}', cc: 'manager@yopmail.com, tmquoc@tma.com.vn', from: '', replyTo: '', subject: '${BUILD_TAG}'
        }
    }
}