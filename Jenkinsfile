pipeline {
    agent none
    stages {
        stage('Display Jenkins Agent Setup') {
            steps {
                sh '''
                    python3 --version
                    pip3 --version
                    printenv | sort
                    pwd
                    ls -al
                '''
            }
               }
        stage('Run schemachange') {
            steps {
                sh "pip3 install schemachange --upgrade"
                sh "schemachange -f migrations -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
            }
        }
    }
}