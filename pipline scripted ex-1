node{
    // tool function returns home location of this tool
    def mvnHome = tool name: 'maven3', type: 'maven'
    
    stage('SCM Checkout'){
       git 'https://github.com/abhisekh89/webapp.git'
       echo 'Code cloning completed'
    }
    
    stage('Maven Build'){
        sh  script: "${mvnHome}/bin/mvn  clean package"
        echo 'Build completed & preparing for next phase'
    }
    
    stage('Deploy Development'){
        echo "Deploy to dev - comming son..."
    }
    
}