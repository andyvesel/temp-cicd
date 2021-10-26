pipeline {
    
    // parameters {
    //     string(name: 'namespace', defaultValue: "${env.JOB_BASE_NAME + '-' + env.BUILD_NUMBER}")
    //     string(name: 'working_branch', defaultValue: 'main')
    //     booleanParam(name: 'stages_failed', defaultValue: false)
    // }
    
    agent { label 'ocp-agent' }

    stages {
        stage('Clone Upstream') {
            steps {
                // checkout scm // add it when switch pipeline source to scm
                sh "ls -la"
                sh "git ls-remote --heads origin"
            }
        }
    }
}
