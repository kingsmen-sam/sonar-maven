node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/itrainavengers/sonar-maven.git'
     }
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn clean compile test'
     }
   }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
         withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
             //sh 'mvn clean package sonar:sonar' 
             sh ' mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=itrainspartans '+ 
             ' -Dsonar.login=fe081245dcecb35f616d678b5dc61153533bdb18 ' +
             ' -Dsonar.links.ci='    
         //}
      }
   }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
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
