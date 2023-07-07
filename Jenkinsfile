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
        
        def MavenHome= tool name: "Maven-Tool", type: "maven"
        
        def mavenCMD= "${MavenHome}/bin/mvn"
        
        sh "${mavenCMD} clean package"
        
    echo "==========================================Built Maven Project============================================"
    
    echo "=========================================Archieving Artifact============================================="
    
        archiveArtifacts artifacts: '**/*.war'
    
    echo "==========================================Artifact Archieved============================================="
        
    }
      
}
