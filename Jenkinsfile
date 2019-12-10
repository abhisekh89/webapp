node{
    // tool function returns home location of this tool
    def mvnHome = tool name: 'maven3', type: 'maven'
    
    stage('SCM Checkout'){
       git credentialsId: 'github', 
	        url: 'https://github.com/abhisekh89/webapp.git', 
	        branch: 'master'
    }
    
    stage('Maven Build'){
        sh  script: "${mvnHome}/bin/mvn  clean package"
    }
    
    stage('Deploy Development'){
        echo "Deploy to dev - comming son..."
    }
    
}