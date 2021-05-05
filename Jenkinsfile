pipeline {
    agent {label 'CISlave'}
    stages{
        stage('run staging playbook'){
            steps{
                sh 'ansible-playbook -i inventory prod.yml --extra-vars "url=${okta_url} id=${okta_id} secret=${okta_secret} db_host=${db_fqnd} pass=${db_password} user=${db_user} username=${username} api_key=${api_key}"'            
            }
        }
        stage('run prod playbook'){
            input {
                message "Should we deploy to production?"
            }
            steps{
                sh 'ansible-playbook -i inventory prod.yml --extra-vars "url=${okta_url} id=${prod_id} secret=${prod_secret} db_host=${prod_host} pass=${db_password} user=${db_user} username=${username} api_key=${api_key}"'            
            }
        }
    }
}

