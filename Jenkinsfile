pipeline {
	agent any 
	stages {
		stage ('clone the repo') {
			steps {
				echo "clone the repo"
 				sh 'rm -rf Jenkins'
				sh 'git clone https://github.com/aashish20010/Jenkins.git'
				}
		}
		
		stage ('push repo to remote host') {
 			steps {
				echo "connect to remote host and pull down the latest version"
				sh '  ssh -i "/var/jenkins_home/workspace/Mailgateway.pem" ec2-user@ip-172-31-24-118.ap-southeast-1.compute.internal                                    git -C "/var/www/html/Testing" pull'
				}
		}
	
		stage ('check website is up') {
			steps {
          			echo "check website is up"
 				sh   'curl -is | head -n 1'
				}
		}
  	}
}
