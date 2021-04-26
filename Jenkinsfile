pipeline {
    agent {label 'CISlave'}
    stages{
        stage('run prod playbook'){
            steps{
                sh "ansible-playbook staging.yml"            
            }
        }
    }
}
    //agent {label 'CISlave'}
    // stages {
    //     stage('get artifact'){
    //         steps{
    //             copyArtifacts(projectName: 'weightCI', filter: "latest.zip")
    //             unzip zipFile: "latest.zip"
    //         }
    //     }
    //     stage('Build env') {
    //         steps {
    //             sh "bash buildEnv.sh -u ${okta_url} -i ${okta_id} -s ${okta_secret} -h ${db_fqnd} -p ${db_password} -n ${db_user}"
    //         }
    //     }
    //      stage('Build dependencies') { 
    //         steps {
    //             sh "curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -"
    //             sh "sudo apt-get install -y nodejs"
    //             sh "sudo npm install cjs"
    //             sh "sudo npm install pm2 -g"
    //         }
    //     }
    //     stage('Deploy'){
    //         steps{
    //             sh "npm run initdb"
    //             sh "sudo pm2 delete all || true"
    //             sh "sudo pm2 start src/index.js"
    //             sh "sudo pm2 save"
    //             sh "sudo pm2 startup"
    //         }
    //     }
    //}
//}
