pipeline {
    agent any
    environment {
//         GCLOUD_CREDS = credentials('credential')
//         PROJECT_ID = 	'student-project-379814'
        CLUSTER_NAME = 'dev-eks'
        LOCATION = 'us-east-1'
        CREDENTIALS_ID = 'awsnargiza'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master', credentialsId: 'github', url: 'https://github.com/Zhakyp01/ctf.git'
            }
        }
        stage('Deploy to kubernetes'){
          steps{
             
             step([$class: 'KubernetesEngineBuilder',  clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'dep.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
		   echo "Deployment Finished ..."
          }
        }
    }
}
