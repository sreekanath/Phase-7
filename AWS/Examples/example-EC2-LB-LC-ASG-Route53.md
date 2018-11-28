Create an image:

	1. Create Ubuntu instance.

	2. Install apache, awscli

		apt-get update -y && apt-get install apache2 awscli -y

	3. Create User. (Programatic)

	4. AWS configure

	5. Create S3 bucket.
		aws s3api create-bucket --bucket svn-apache-backup --region us-east-2 --create-bucket-configuration LocationConstraint=us-east-2

	6. Configure crontab.
	https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/

	aws s3 ls svn-apache-backup
	ls /var/www/html/

	crontab -e

	* * * * * aws s3 cp /var/www/html/ s3://svn-apache-backup/ --recursive
	* * * * *  sleep 10; aws s3 cp /var/www/html/ s3://svn-apache-backup/ --recursive
	* * * * * aws s3 cp s3://svn-apache-backup/ /var/www/html/ --recursive
	* * * * *  sleep 10; aws s3 cp s3://svn-apache-backup/ /var/www/html/ --recursive
	@reboot echo "<center><h1>I am from the host $(curl ifconfig.me)" > /var/www/html/index.html

	Or we can use sync instead of cp
	* * * * * aws s3 sync /var/www/html/ s3://svn-apache-backup/
	* * * * *  sleep 10; aws s3 sync /var/www/html/ s3://svn-apache-backup/

	7.Create image.

FYI:
	https://www.cloudns.net/blog/10-most-used-nslookup-commands/

	nslookup google.com

	nslookup -type=soa google.com

	nslookup -type=mx google.com

	nslookup -type=any google.com

	nslookup -type=ns google.com

	nslookup -type=ns svnreddydevops.com
	nslookup -type=soa svnreddydevops.com
	nslookup -type=any svnreddydevops.com

Create Load Balancer(LB):

Create Launch Configure(LC): Choose our own AMI which we created above.

Create Autosacale group using LS:

Attach the LB to ASG.

Add the LB to Route53.
