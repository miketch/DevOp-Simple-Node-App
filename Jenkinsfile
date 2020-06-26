node {
    def application


    stage('Clone Stage') {
        checkout scm
    }

    stage('Linting') {
        sh 'pwd'
        sh 'standard "**/*.js"'
    }
    
    stage('Build Image') {
        application = docker.build("miketch/simple-node-app:v1")
    }


    stage('Push Image to AWS') {
        sh 'aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 850598408435.dkr.ecr.us-west-2.amazonaws.com'
        sh 'docker tag miketch/simple-node-app:v1 850598408435.dkr.ecr.us-west-2.amazonaws.com/simple-node-app:v1'
        sh 'docker push 850598408435.dkr.ecr.us-west-2.amazonaws.com/simple-node-app:v1'

    }
    
    stage('Deploy') {

        withAWS(region:'us-west-2', credentials:'ecr_credentials') {
					sh '''
                        kubectl set image deployments/simple-node-app simple-node-app=850598408435.dkr.ecr.us-west-2.amazonaws.com/simple-node-app:v1
					'''
		}
       
    }
    
}