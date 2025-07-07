# Cloud-Security-with-AWS-IAM

# Objective

This project demonstrates the use of AWS Identity and Access Management (IAM) to securely manage user access to cloud resources. I launched an EC2 instance and implemented IAM policies and user groups to define and enforce authentication and authorization rules. The project showcases best practices in cloud security by ensuring that only authorized users have access to specific AWS services, following the principle of least privilege.

<img width="1024" height="755" alt="Image" src="https://github.com/user-attachments/assets/a0f6b372-07ee-4d42-9a05-60b62c7db83c" />

# Tagging for Secure Resource Management in AWS

<img width="979" height="605" alt="Image" src="https://github.com/user-attachments/assets/9295faf4-d793-43f6-841d-38a0c599aef6" />

To support secure cloud resource organization and improve operational efficiency, I implemented tagging on Amazon EC2 instances using AWS best practices. I used the tag key "Env" (short for Environment) with values such as "Production" and "Development" to classify instances by function and sensitivity. 

These metadata tags play a critical role in resource governance, enabling streamlined access control, cost allocation, and incident response. Tag-based identification enhances visibility across environments, supports automated security auditing, and assists in applying least privilege policies through Identity and Access Management (IAM). This approach aligns with cybersecurity principles for scalable, secure cloud infrastructure.

# IAM Policies Implementation for Secure EC2 Access

<img width="1134" height="750" alt="Image" src="https://github.com/user-attachments/assets/1c33446e-4cd0-4380-9ea9-a8abb8a1410c" />

As part of a cloud access control project, I created and implemented a custom IAM policy using JSON to enforce the principle of least privilege for Amazon EC2 instances. The policy was designed to grant an intern-level user full permissions to interact with instances tagged as "development", while restricting critical actions such as tag creation and deletion.

This JSON-based policy leveraged key IAM components:

- Effect: Set to "Allow" to grant specific permissions
- Action: Included operations like ec2:StartInstances and ec2:DescribeInstances
- Resource: Scoped to EC2 instances using Amazon Resource Names (ARNs)

By using structured JSON syntax, I was able to precisely define what users could do, to which resources, and under what conditions. Tag-based controls (e.g., using the "Env" tag) helped enforce role-based access control (RBAC) and enhanced security governance.

# AWS Account Alais Configuration for Enahanced Console Accessibility
<img width="963" height="689" alt="Image" src="https://github.com/user-attachments/assets/ee92ced8-a0b3-433a-9dbc-96fa645e10d5" />

As part of IAM configuration best practices, I created an AWS Account Alias to simplify secure access to the AWS Management Console. Instead of relying on a lengthy numeric account ID, I assigned a user-friendly alias, which is now embedded in the custom sign-in URL for my AWS environment.

This quick setup (under 30 seconds) was performed through the IAM dashboard and demonstrates attention to identity personalization, usability enhancements, and administrative efficiency. Although simple, using an alias is a recommended practice that improves the sign-in experience for users and teams, especially in multi-account or enterprise environments.

# IAM Users, Groups, and Role-Based Access Control in AWS
<img width="3440" height="1440" alt="Image" src="https://github.com/user-attachments/assets/87175d8a-95d9-4eeb-875a-4587c0e28817" />
I implemented a secure Identity and Access Management (IAM) framework using IAM users, user groups, and a custom JSON-based IAM policy to enforce role-based access control (RBAC) in AWS. I created a dedicated IAM user group (e.g., DevInternGroup) and attached a scoped policy (NextWorkDevEnvironmentPolicy) that grants limited access only to EC2 instances tagged with "development". Any user added to this group inherits the group-level permissions, simplifying permission management and reducing the risk of privilege escalation.

To simulate real-world onboarding, I created an IAM user, securely shared sign-in credentials, and logged in as that user to validate access boundaries. As expected, the user was denied access to all AWS console panels except for the assigned EC2 development environment, confirming that least privilege was properly enforced.

# Verifying IAM Permissions: Stopping the Development Instance 

<img width="3440" height="1440" alt="Image" src="https://github.com/user-attachments/assets/c549f664-9c8d-401b-beab-ad63df8080b2" />
<img width="3424" height="1403" alt="Image" src="https://github.com/user-attachments/assets/468a7e62-6007-492c-b4bc-59af785c12cb" />
To test the effectiveness of the IAM policy attached to the NextWork-Dev-Group, I attempted to stop two different EC2 instances—one tagged as "production" and the other as "development".

As expected, access to stop the production instance was denied, reflecting the enforced restrictions defined in the JSON policy. However, when switching to the development instance, the action succeeded, and the instance state changed from Stopping to Stopped.

This validated that the policy was correctly configured to only allow the ec2:StopInstances action on instances tagged with "development", demonstrating tag-based access control and proper implementation of the principle of least privilege.

# Validating Access with IAM Policy Simulator
<img width="3440" height="1440" alt="Image" src="https://github.com/user-attachments/assets/3e249e2b-c271-481e-8cf6-951591d8e151" />

To ensure the accuracy and security of my IAM configurations, I used the IAM Policy Simulator, a tool provided by AWS that allows for safe, pre-deployment testing of IAM policies. This tool is critical for identifying policy misconfigurations such as missing permissions or improperly scoped resources, and it supports the enforcement of the principle of least privilege without affecting production environments.

# How I used the Simulator 
I tested whether the devuser group had permission to perform actions such as ec2:StopInstances and ec2:DeleteTags. Initially, both actions were denied due to the policy not correctly targeting the EC2 resources. By adjusting the resource scope in the JSON policy to include only instances tagged with "development", the StopInstances action was successfully authorized, while DeleteTags remained restricted—exactly as intended.

This validation step confirmed that my policy logic was functioning properly and emphasized the importance of tag-based access control and explicit permission boundaries in AWS security practices.

# Summary 
This project demonstrated how to design and implement a secure, scalable Identity and Access Management (IAM) framework in AWS using IAM users, groups, custom JSON policies, account aliases, tagging strategies, and policy validation tools like the IAM Policy Simulator. I successfully applied the principle of least privilege by restricting user permissions based on resource tags (e.g., "development" vs. "production"), and verified access behaviors through simulated testing and real-world actions (such as stopping EC2 instances). By combining policy-based access control with tagging and user group management, this project reflects best practices in cloud security, operational governance, and identity lifecycle management.






















