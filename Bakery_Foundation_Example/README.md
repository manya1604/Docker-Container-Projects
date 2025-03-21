# 🚀 Packer-based AMI Creation on AWS 🖥️

## 📌 **Overview**
This experiment demonstrates how to create an Amazon Machine Image (**AMI**) using **Packer** on AWS. Packer automates the AMI creation process, making it efficient, repeatable, and scalable.

---

## 🔧 **Prerequisites**
✔ An AWS account with necessary permissions  
✔ AWS CLI installed and configured  
✔ Packer installed on your system  
✔ A valid IAM user with EC2 and AMI permissions  

---

## 🏗 **Steps to Create an AMI using Packer**

### ✅ **1. Setup AWS Credentials**
Ensure AWS CLI is configured with appropriate access:
```sh
aws configure
```

### ✅ **2. Define the Packer Template**
Create a `packer.json` file with the following configuration:
```json
{
  "variables": {
    "aws_region": "us-east-1"
  },
  "builders": [
    {
      "type": "amazon-ebs",
      "region": "{{user `aws_region`}}",
      "source_ami": "ami-0c55b159cbfafe1f0",
      "instance_type": "t2.micro",
      "ssh_username": "ec2-user",
      "ami_name": "packer-ami-{{timestamp}}"
    }
  ]
}
```

### ✅ **3. Initialize and Validate Packer Configuration**
Run the following command to validate your configuration:
```sh
packer validate packer.json
```

### ✅ **4. Build the AMI**
To create the AMI, execute:
```sh
packer build packer.json
```
![AMI List Screenshot](https://github.com/manya1604/Docker-Container-Projects/blob/main/Bakery_Foundation_Example/Screenshot%202025-03-21%20231942.png)
### ✅ **5. Verify AMI in AWS Console**
Once the build process completes, the newly created AMI can be found in the **AWS EC2 Console** under **Images > AMIs**.

![AMI List Screenshot](https://github.com/manya1604/Docker-Container-Projects/blob/main/Bakery_Foundation_Example/Screenshot%202025-03-21%20225012.png)


### ✅ **6. Launch an EC2 Instance from the AMI**
1. Navigate to the **AWS EC2 Console**
2. Select **Launch Instance**
3. Choose **My AMIs** > Select the newly created AMI
4. Configure instance settings and launch the instance

![AMI List Screenshot](https://github.com/manya1604/Docker-Container-Projects/blob/main/Bakery_Foundation_Example/Screenshot%202025-03-21%20232238.png)
### ✅ **7. Connect to the Instance**
Once the instance is running, connect via SSH:
```sh
ssh -i your-key.pem ec2-user@<public-ip>
```

---

## 🧹 **Cleanup**
To avoid incurring costs, delete the AMI and any associated instances:
```sh
aws ec2 deregister-image --image-id <ami-id>
aws ec2 delete-snapshot --snapshot-id <snapshot-id>
```

---

## 🎯 **Conclusion**
This experiment successfully demonstrates how to use **Packer** to automate AMI creation on AWS, making the process **more efficient and repeatable**.

💡 *By leveraging Packer, you can standardize AMI creation and integrate it into automated DevOps workflows!* 🚀

