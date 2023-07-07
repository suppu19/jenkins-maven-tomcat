node {
    stage('test') {
        echo 'Knowledge Is Free'
    }
        echo "=======================================Checking Out Code from Github======================================="
       
        stage('Git Checkout') {
       
        git branch: 'main', credentialsId: 'Github', url: 'https://github.com/suppu19/project1.git'
       
        echo "=======================================Pulled Code from Github======================================="   
    }
   
    echo "=========================================Building Maven Project=========================================="
   
    stage('Maven Build') {
       
            sh "mvn clean package"
            
    }    
    stage("Archiving Artifact") {        
       
    echo "==========================================Built Maven Project============================================"
   
    echo "=========================================Archiving Artifact============================================="


        archiveArtifacts artifacts: '**/*.war'
   
    echo "==========================================Artifact Archieved============================================="
       
    }
}
stage('Deployment') {
sshagent(['tomcat-server']) {
sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/scripted-pipeline/target/maven-web-applicaton.war ubuntu@13.250.105.104:/opt/tomcat/webapps"
       }
}
