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
            sh "apt-get install -y jq"
            sh "apt-get install -y nkf"
            sh "apt-get install -y openssl"
        }
        
        stage('Setup') {
            sh ""
        }

        stage('Data') {
            sh "chmod +x tweet.sh"
            sh "./tweet.sh help"
        }
    }
}
