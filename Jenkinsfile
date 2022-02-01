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
				sh '  ssh -i "/var/jenkins_home/workspace/Mailgateway.pem" ec2-user@ip-172-31-25-76.ap-southeast-1.compute.internal                                 sudo  git -C "/var/www/html/Jenkins" pull origin master'
				}
		}
	
		stage ('check website is up') {
			steps {
          			echo "check website is up"
 				sh   'curl `ip a | grep eth0 | tail -n1 | cut -b 10-21`'
				}
		}
  	}
}
