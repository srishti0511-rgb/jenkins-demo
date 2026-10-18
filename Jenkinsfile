pipeline {
 agent any
 stages {
 stage('Checkout') {
 steps { checkout scm }
 }
 stage('Build') {
 steps {
 echo 'Building HTML project...'
 bat 'if not exist index.html exit /b 1'
 }
 }
 stage('Test') {
 steps {
 echo 'Testing HTML project...'
 bat 'findstr /C:"Welcome to Jenkins" index.html'
 }
 }
 stage('Deploy') {
 steps {
 echo 'Preparing deployment artifact...'
 bat 'if not exist deploy mkdir deploy'
 bat 'copy /Y index.html deploy\index.html'
 archiveArtifacts artifacts: 'deploy/index.html'
 }
 }
 }
 post {
 success { echo 'CI/CD Pipeline Successful!' }
 failure { echo 'CI/CD Pipeline Failed!' }
 }
}
