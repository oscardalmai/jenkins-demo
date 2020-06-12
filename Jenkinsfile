pipeline {
  agent any
  stages {
    stage('Print Branch Name') {
      steps {
        echo "BRANCH_NAME = ${env.BRANCH_NAME}"
      }
    }
    
    stage('Update Project') {
      steps {
        ansibleTowerProjectSync(towerServer: 'AWX TEST', towerCredentialsId: '5372add5-75b6-4f30-8dbc-8e5dc7eebdac', project: 'Jenkins Demo', importTowerLogs: true)
      }
    }

    stage('Workflow execution') {
      steps {
        ansibleTower(towerServer: 'AWX TEST', towerCredentialsId: '5372add5-75b6-4f30-8dbc-8e5dc7eebdac', jobTemplate: '27', jobType: 'run', templateType: 'workflow', importWorkflowChildLogs: true, importTowerLogs: true, scmBranch: "${env.BRANCH_NAME}")
      }
    }
  }
}
