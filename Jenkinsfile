@Library(['github.com/indigo-dc/jenkins-pipeline-library@release/2.3.0']) _

def projectConfig

pipeline {
    agent any

    stages {
        stage('SQA baseline dynamic stages: qc-style') {
            steps {
                script {
                    projectConfig = pipelineConfig(
                        configFile: './.sqa/config_qc_style.yml'
			validatorDockerImage: 'eoscsynergy/jpl-validator:2.4.0'
                    )
                    buildStages(projectConfig)
                }
            }
            post {
                cleanup {
                    cleanWs()
                }
            }
        }
        stage('SQA baseline dynamic stages: qc-doc') {
            when {
                anyOf {
                    branch 'refs/heads/*'
                    buildingTag()
                    not { changeRequest() }
                }
            }
            steps {
                script {
                    projectConfig = pipelineConfig(
                        configFile: './.sqa/config_qc_doc.yml',
                        scmConfigs: [ localBranch: true ]
                    )
                    buildStages(projectConfig)
                }
            }
            post {
                cleanup {
                    cleanWs()
                }
            }
        }
    }
}
