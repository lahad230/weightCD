pipeline {
    agent {label 'staging'}
    stages {
        stage('get artifact'){
            steps{
                copyArtifacts(projectName: 'weightCI', selector: specific("latest"))
                unzip zipFile: "latest.zip"
            }
        }
         stage('Build dependencies') { 
            steps {
                sh "curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -"
                sh "sudo apt-get install -y nodejs"
                sh "sudo npm install cjs"
                sh "sudo npm install pm2 -g"
            }
        }
        stage('Deploy'){
            steps{
                sh "sudo pm2 delete all || true"
                sh "sudo pm2 start src/index.js"
                sh "sudo pm2 save"
                sh "sudo pm2 startup"
            }
        }
    }
}