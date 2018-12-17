Example with ELB

1. Image(AMI) where DevOpsWebApp deployed to tomcat. Refer to install tomcat: https://github.com/DevOpsPlatform/Phase-1/blob/master/tomcat9-setup-on-ubuntu.md

2. Create two instances with same AMI.

3. Create Application Load Balancer as to target the two instances.

4. Create **CloudFront Distributions**, with `Origin Path` as **/DevOpsWebApp-1.0.0** AND `Default Root Object` as **index.jsp**.

5. Choose other default values.

6. Create **CloudFront Distributions**, this might take 5 to 10 mins.

7. once the status is **Deployed**, then copy the domain name and launch it in any browser any where.

![image](https://user-images.githubusercontent.com/24622526/50066453-d8518000-01e1-11e9-8277-77118f01a1ef.png)


8. First disbale the distribution, and then delete once the status is **Deployed**.
