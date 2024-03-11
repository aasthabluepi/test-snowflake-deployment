pipeline {
    agent any
    stages {
        stage('Display Jenkins Agent Setup') {
            steps {
                sh '''
                    apt install curl
                    python3 --version
                    printenv | sort
                    pwd
                    ls -al
                    free -m
                    free -g
                '''
            }
               }
        stage('Run schemachange') {
            steps {
                sh "pip install schemachange --upgrade"
                sh "schemachange -f migrations -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
            }
        }
    }
}