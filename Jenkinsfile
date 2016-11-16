#!groovy

node {
    stage('checkout') {
      checkout scm
    }
    stage('upload') {
      def branchName = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
      def servers = [
        'dev': 'devhost',
        'test': 'testhost',
        'staging': 'staginghost',
        'master': 'masterhost'
      ]
      def host = servers[branchName]
      def port = 80
      echo "http://$host:$port/crx/packmgr/service.jsp"
    }
}
