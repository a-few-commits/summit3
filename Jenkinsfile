def gitCommit() {
    sh "git rev-parse HEAD > GIT_COMMIT"
def gitCommit = readFile('GIT_COMMIT').trim()
    sh "rm -f GIT_COMMIT"
    return gitCommit
}

node {
    stage('Checkout') {
       checkout scm
    }
    
    stage('Get Data') {
        sh "apt-get install curl"
    }
}
