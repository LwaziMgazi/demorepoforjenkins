def mvnHome
node('node'){
   stage('git checkout by Lwazi'){
     git credentialsId: 'git-token', url: 'https://github.com/LwaziMgazi/demorepoforjenkins.git'
   }
   stage('maven test'){
     try{
       mvnHome=tool 'maven-3.6.3'
       sh "$mvnHome/bin/mvn --version"
       sh "$mvnHome/bin/mvn clean test surefire-report:report"
     }catch(err){
        sh "echo error in defining mav"
     }
   }
   stage('test case and report'){
     try{
       echo "executing test"
     }catch(err){
       echo err
     }
   }
   stage('package and generate artifacts'){
     try{
       sh "$mvnHome/bin/mvn clean package -DiskipTests=true."
       archiveArtifacts allowEmptyArchive: true, artifacts: 'addressbook_main/*.txt'
     }catch(err){
       echo err
     }
   }
}
