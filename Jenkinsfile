node('aws-ec2') {

    stage('clone') {
        git 'https://github.com/shivi-bit/go-repo.git'
    }

    stage('build') {
        sh 'sudo docker build -t shivangani/go-app:${BUILD_NUMBER} .'
    }

    stage('publish') {
        sh 'sudo docker push shivangani/go-app:${BUILD_NUMBER}'
    }

}

node('k8s-node') {
    
    stage('deploy') {
        git 'https://github.com/shivi-bit/go-repo.git'
        sh 'kubectl apply -f deployment.yml -n go-application'
    }
}

