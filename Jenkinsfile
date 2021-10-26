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
                catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
                    script {
                        working_branch = 'git ls-remote --heads origin | grep $(git rev-parse HEAD) | cut -d / -f 3'
                    }
                }
                sh 'echo ${working_branch}'
            }
        }
        stage ('Create project') {
            steps {
                script {
                    if ( currentBuild.result != null ) { stages_failed = true; return; }
                        catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
                            openshift.withCluster(){
                            openshift.newProject(namespace)
                        }
                    }
                }
            }
        }
    }
}
