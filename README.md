AMAZIN INC PCI DSS COMPLIANT INFRASTRUCTURE
---
---


## What is PCI DSS?
![PCI DSS](/images/pci-logo.jpeg)

It is abundantly clear that the world has made great strides in regards to both the increasing use of technology such as online payments on ecommerce platforms, and data and in relation to data privacy and protection regulations. Data privacy and data security go hand in hand(or glove) and are complementary and both necessary today.

_PCI DSS_ is an acronym for Payment Card Industry Data Security Standard. This is a standard (not a law) set up by competing payment processors such as VISA, Mastercard, AMEX and Discover to control or mitigate risks associated with merchants accepting sensitive cardholder data in their systems and to ensure these businesses maitain safe processes that safeguard cardholder data.

It is to be noted that even though PCI DSS isn't a law, there is an obligation for businesses, whether they are small merchants or a large global bank, to align with the PCI DSS for both legal and regulatory obligations as the potential fallout of noncompliance may include significant fines, huge costs of data breaches and loss of customer confidence in your services/business which may even cause it to fold.


## PCI DSS Requirements.
_PCI DSS_ is composed of 6 milestones that businesses e.g online merchants like Amazin Inc have to reach.
1. Remove sensitive authentication data and limit data retention. If sensitive authentication data and other cardholder data are not stored, the effects of a compromise will be greatly reduced.
2. Protect systems and networks, and be prepared to respond to a system breach.
3. Secure payment card applications.
4. Monitor and control access to your systems.
5. Protect stored cardholder data.
6. Finalize remaining compliance efforts, and ensure all controls are in place. So all remaining related policies, procedures and processes needed to protect cardholder data environment must be finalized.


PCI DSS divides these 6 milestones into 12 requirements to achieve the milestones, namely:
1. Install and maintain a firewall configuration to protect cardholder data.
2. Do not use vendor-supplied defaults for system passwords and other security parameters.
3. Protect stored cardholder data.
4. Encrypt transmission of cardholder data across open, public networks.
5. Use and regularly update anti-virus software and programs.
6. Develop and maintain secure systems and applications.
7. Restrict access to cardholder data by business need to know.
8. Assign a unique ID to each person with computer access.
9. Restrict physical access to cardholder data.
10. Track and monitor all access to network resources and cardholder data.
11. Regularly test security systems and processes.
12. Maintain a policy that addresses information security for all personnel.

The above represents all the important aspects of PCI DSS but it is important to note that each requirement has sub-requirements to it. Read [PCI DSS](https://www.pcisecuritystandards.org/document_library) and on Wikipedia [PCI DSS Wiki](https://en.wikipedia.org/wiki/PCI_DSS).


# MY SOLUTION FOR AMAZIN:

## Problem:

A company, Amazin wants to set up an ecommerce platform that accepts users' credit card info.
My solution to this problem is to make it as composable(divisible into easily understood concepts) as possible.

## Solution:

I have gone in depth more in my proposal.pdf file located in the root directory of this GitHub repository.

Generally:

1. _Limit the scope of PCI DSS Compliance/assessment._

   My recommendation is that Amazin Inc outsources the storage and processing of their customer's card data as well as the tokenization process to another company such as a payment aggregator or payment gateway, of which there are numerous(they include Stripe, Square, Razorpay, Instamojo, CCAvenue, among others)or even that they use a dedicated merchant account.

   Network Segementation with Amazon VPCs and security groups is necessary to ensure that the scope of PCI compliance is small. This is important to ensure other infrastructure is not put into scope.
2. Elastic Load Balancing (ELB): ELB increases the speed of networked processes through distributing the requests to several servers. ELB also allows additional encryption layers for enhanced security.
3. Firewalls and VPNs.
4. Protect and restrict user (system admins or anyone else with access) accounts and scope.
5. Use and update Antivirus.
6. Logging (e.g logging any change in the infrastructure and code landscapes).
7. File system Integrity and Intrusion detection systems.


Amazin Inc as a startup can use various open source tools as well as proprietary AWS tools to meet compliance requirements. These include: 
> i. Using Terraform and Packer to build immutable infrastructure so that we never make changes to running production instances.

> ii. Protect AWS IAM accounts and apply multifactor auth(MFA). Never use root AWS account

> iii. Using OpenVPN, OpenLDAP and Duo Security(a 3rd party MFA tool) to provide a secure path to running AWS EC2 instances(which have the client payment processing apps), offer secure passwords, history of login attempts, user control, and multi-factor authentication.

> iv. Using OSSEC or Samhain for file integrity and host-based Intrusion detection(IDS).

> v. Using Snort for network-based IDS.

> vi. Using Clam-AV antivirus

> vii. Amazon AWS CloudWatch for centralized logging.

> viii. AWS KMS to protect and rotate any keys used by our instances.

---
## LOGICAL DIAGRAMS OF ARCHITECTURE:

![Overall Arch](/images/Subnets.png)


## VPC1:

![VPIC1](/images/vpc1.png)


## VPC2:

![VPC2](/images/monitoring_metrics.png)

## VPC3:

![VPC3](/images/vpc3.png)


