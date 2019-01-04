def gitCommit() {
    sh "git rev-parse HEAD > GIT_COMMIT"
def gitCommit = readFile('GIT_COMMIT').trim()
    sh "rm -f GIT_COMMIT"
    return gitCommit
}

node {
    sh "dockerd &"
    docker.image('ubuntu').inside {
        stage('Checkout') {
            checkout scm
        }
        
        stage('Dependencies') {
            sh "apt-get update"
            sh "apt-get install -y curl"
        }

        stage('Data') {  
            sh "curl --help"
        }
    }
}
