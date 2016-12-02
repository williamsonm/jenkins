#!groovy

properties([
  [ $class: 'jenkins.model.BuildDiscarderProperty'
  , strategy: [$class: 'LogRotator', numToKeepStr: 5]
  ]
, pipelineTriggers([cron('H/15 * * * *')])
])

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
    stage('color') {
      ansiColor('xterm') {
				def RED='\033[0;31m'
				def NC='\033[0m'
				sh "echo 'I ${RED}love${NC} Stack Overflow\n'"
      }
    }
}
