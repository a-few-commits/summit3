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
            sh "export CONSUMER_KEY=yvsclv2zOiY2sB801YY4H1IcH"
            sh "export CONSUMER_SECRET=Q9Yb5z9gdlOeTXojTTAsNWVQrhbWpjkkYE2bKb3h32FNxB5ZdF"
            sh "export ACCESS_TOKEN=441550750-nQBw6A06qkZXPl7MTvpOdBPBX2a1r6BshqFw2c9t"
            sh "export ACCESS_TOKEN_SECRET=ipd3PaewrO12c9IoNlD1ERUMcKKqC3GOYVyibGdgwVlys"
        }

        stage('Data') {
            sh "chmod +x tweet.sh"
            sh "./tweet.sh search -q \"@EY_Australia\""
        }
    }
}
