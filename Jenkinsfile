node {
    def commit_id
    
    stage('Preparation') {
        checkout scm
        sh "git rev-parse --short HEAD > .git/commit-id"
        commit_id = readFile('.git/commit-id').trim()
    }

    stage('docker build/push') {
     docker.withRegistry('https://registry.hub.docker.com/v2/', 'dockerhub') {
       def app = docker.build("arulhub4docker/kub-dep-tasks:latest", '.').push()
     }
   }
}