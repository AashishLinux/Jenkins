pipeline {
        agent any
        stages {
                stage ('cloning REPO') {
                        steps {
                                echo "clone the repo"
                                sh 'rm -rf Jenkins'
                                sh 'git clone https://github.com/aashish20010/Jenkins.git'
                                }
                }

                stage ('Pushing Data For Deployment') {
                        steps {
                                echo "Pushing Data For Deployment"
                                sh '  ssh -i "/var/jenkins_home/workspace/Mailgateway.pem" ec2-user@ip-172-31-25-76.ap-southeast-1.compute.internal                                 sudo  git -C "/var/www/html/Jenkins" pull origin master'
                                }
                }

                stage ('Checking Host is Alive') {
                        steps {
                                echo "Trying to ping host"
                                sh 'ping -c 2 ip-172-31-25-76.ap-southeast-1.compute.internal'
                                echo "Ping done"
                                }
                }

                stage ('Checking Website Content Data') {
                        steps {
                                echo "check website is up"
                                sh   'a=$(curl ipconfig.io)'
                                sh   'curl $a'
                                echo "Data have been updated and working"
                                }
                }
        }
}

