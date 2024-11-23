pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '04e021da-62f6-462b-b47e-4472004f44b3', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd-jk', war: '**/*.war' }
 }
 }
 }
}
