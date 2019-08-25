node {
    stage('Code Checkout') { // for display purposes
     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/kingsmen-sam/sonar-maven.git']]])
     }
   stage('Build Test & Package') {
      echo 'Build the package'
     withMaven(jdk: 'Java', maven: 'Maven') {
       sh 'mvn clean compile test'
     }
   }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
        withMaven(jdk: 'Java', maven: 'Maven')  {
             //sh 'mvn clean package sonar:sonar' 
             sh 'mvn clean verify sonar:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=itrainspartans '+ 
             ' -Dsonar.login=fe081245dcecb35f616d678b5dc61153533bdb18 ' +
             ' -Dsonar.links.ci='    
         //}
      }
   }
   stage('Artifacts') {
       echo 'package the project artifacts..'
        withMaven(jdk: 'Java', maven: 'Maven')  {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
      stage('Test Automation'){
       echo 'Deploy to Dev environment'
   }
   
}
