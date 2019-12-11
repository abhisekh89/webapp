pipeline{
    agent any
    environment{
	  PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
	}
    stages{
        stage('SCM Checkout'){
            steps{
                git url: 'https://github.com/abhisekh89/webapp.git',
                branch: 'master',
                credentialsId: 'github'
            }
        }

        stage('Maven Build'){
            steps{
                sh 'mvn clean package'
            }
        }

        stage('Deploy Dev'){
            steps{
                sshagent(['tomcat-dev']) {
                    // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@52.66.207.57 /opt/tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/WebApp.war  ec2-user@52.66.207.57:/opt/tomcat8/webapps/"
                    // start tomcat
                    sh "ssh ec2-user@52.66.207.57 /opt/tomcat8/bin/startup.sh"
                } 
            }
        }
    }
}