
pipeline {
agent any
// tools{
// maven 'MAVEN_HOME'
// }
stages {
stage('Build Application') {
steps {
dir('C:\Users\CSIVANI\AnypointStudio\studio-workspace\mule-jenkins-deployment-api') {
// some block
echo 'Cleaning'
bat 'mvn clean install'
}
}
}
stage('Test') {
steps {
dir('C:\Users\CSIVANI\AnypointStudio\studio-workspace\mule-jenkins-deployment-api') {
// some block
echo 'Application in Testing Phase…'
bat 'mvn test'
}
}
}
stage('Deploy CloudHub'){
  environment {

ANYPOINT_CREDENTIALS = credentials(‘anypointPlatform’)

}
steps{
dir('C:\Users\CSIVANI\AnypointStudio\studio-workspace\mule-jenkins-deployment-api'){
bat 'mvn sonar:sonar'
}
}
}
stage('deploy') {
steps {
dir('C:\Users\CSIVANI\AnypointStudio\studio-workspace\mule-jenkins-deployment-api') {
// some block
echo ‘Deploying mule project due to the latest code commit…’

echo ‘Deploying to the configured environment….’
mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=7.12.0 -Danypoint.username=ssivani -Danypoint.password=Mule2022 -Denv=Sandbox -Dappname=mule-jenkins-deployment-api -Dbusiness=MuleSoft -Dvcore=Micro -Dworkers=1 -DaltDeploymentRepository=myinternalrepo::default::file:///C:\snapshots
}
}
}
}
}
