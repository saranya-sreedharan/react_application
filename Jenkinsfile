node {
    stage('Code checkout') {
        echo 'Code checkout from the repository'
        git 'https://github.com/saranya-sreedharan/react_application'
    }

    stage('Containerizing react_app') {
        echo 'Containerizing react_app'
        sh 'sudo docker build -t sarus23/my-react_app:1.0 .'
    }

    stage('Pushing Docker image') {
        echo 'Pushing Docker image to Docker Hub'
        def dockerHubCredentials = 'docker-hub-credentials'
        withCredentials([usernamePassword(credentialsId: dockerHubCredentials,
                                         usernameVariable: 'DOCKER_USERNAME',
                                         passwordVariable: 'DOCKER_PASSWORD')]) {
            sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
            sh 'docker push sarus23/my-react_app:1.0'
        }
    }
}
