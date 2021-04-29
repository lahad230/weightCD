pipeline {
    agent {label 'CISlave'}
    stages{
        stage('run staging playbook'){
            steps{
                sh 'ansible-playbook staging.yml --extra-vars "url=${okta_url} id=${okta_id} secret=${okta_secret} db_host=${db_fqnd} pass=${db_password} user=${db_user} username=${username} api_key=${api_key}"'            
            }
        }
        stage('run prod playbook'){
            input {
                message "Should we deploy to production?"
            }
            steps{
                sh 'ansible-playbook prod.yml --extra-vars "url=${okta_url} id=${prod_id} secret=${prod_secret} db_host=${prod_host} pass=${db_password} user=${db_user} username=${username} api_key=${api_key}"'            
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
