pipeline {
    
    parameters {
        string(name: 'namespace', defaultValue: "${env.JOB_BASE_NAME + '-' + env.BUILD_NUMBER}")
        string(name: 'working_branch', defaultValue: 'main')
        booleanParam(name: 'stages_failed', defaultValue: false)
    }
    
    agent { label 'ocp-agent' }

    stages {
        stage('Clone Upstream') {
            steps {
                script {
                    working_branch = 'git ls-remote --heads origin | grep $(git rev-parse HEAD) | cut -d / -f 3'
                }
                sh '${working_branch}'
            }
        }
    }
}
