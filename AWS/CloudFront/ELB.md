Example with ELB

1. Image(AMI) where DevOpsWebApp deployed to tomcat. Refer to install tomcat: https://github.com/DevOpsPlatform/Phase-1/blob/master/tomcat9-setup-on-ubuntu.md

2. Create two instances with same AMI.

3. Create Application Load Balancer as to target the two instances.

4. Create **CloudFront Distributions**, with `Origin Path` as **/DevOpsWebApp-1.0.0** AND `Default Root Object` as **index.jsp**.

![image](https://user-images.githubusercontent.com/24622526/50066908-5c0c6c00-01e4-11e9-99c4-00d716d6f315.png)

![image](https://user-images.githubusercontent.com/24622526/50066955-91b15500-01e4-11e9-9ba5-7e6261161e33.png)

![image](https://user-images.githubusercontent.com/24622526/50066997-c6bda780-01e4-11e9-94bc-a7021e5150a5.png)

![image](https://user-images.githubusercontent.com/24622526/50067028-ee147480-01e4-11e9-834b-4e4cad586773.png)

5. Fill the details as shown in above images, and choose other default values.

6. Create **CloudFront Distributions**, this might take 5 to 10 mins.

7. Once the status is **Deployed**, then copy the domain name and launch it in any browser any where.

![image](https://user-images.githubusercontent.com/24622526/50066453-d8518000-01e1-11e9-8277-77118f01a1ef.png)


8. First **Disbale** the distribution, and then delete once the status is **Deployed**.
