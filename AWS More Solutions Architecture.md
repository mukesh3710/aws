# AWS More Solutions Architecture

---
# AWS Solutions Architecture Steps for Blocking an IP Address

## Blocking an IP Address
1. **Create a Network ACL (NACL):**
   - Navigate to the VPC console in AWS Management Console.
   - Select "Network ACLs" from the navigation pane.
   - Choose or create a new NACL and associate it with your subnet.
   - Add an inbound rule to deny traffic from the specific IP address:
     - Rule Number: A unique number (e.g., 100).
     - Type: Custom or specific protocol (e.g., HTTP).
     - Protocol: TCP or All Traffic.
     - Port Range: Specific or all ports.
     - Source: The IP address to block (e.g., `192.168.1.1/32`).
     - Action: Deny.

2. **Test the Configuration:**
   - Use tools like `curl` or a web browser to verify that the blocked IP address cannot access the resources.

---

## Blocking an IP Address – with an ALB
1. **Modify Security Groups:**
   - Go to the EC2 console and select "Security Groups."
   - Locate the security group associated with your Application Load Balancer (ALB).
   - Add an inbound rule to block the IP address:
     - Type: Custom.
     - Protocol: TCP.
     - Port Range: Specific or all ports.
     - Source: The IP address to block (e.g., `192.168.1.1/32`).
     - Action: Deny.

2. **Test the ALB:**
   - Confirm that requests from the blocked IP address cannot access resources served by the ALB.

---

## Blocking an IP Address – with an NLB
1. **Create an NLB Rule:**
   - Open the EC2 console and navigate to "Load Balancers."
   - Select your Network Load Balancer (NLB).
   - Update the target group:
     - Configure a listener rule in the NLB to block requests from a specific IP address.

2. **Use Security Groups or NACLs:**
   - Attach a security group or modify a NACL to block traffic from the specific IP address.

3. **Verify the Configuration:**
   - Test using the blocked IP address to ensure traffic is denied.

---

## Blocking an IP Address – ALB + WAF
1. **Create a Web ACL:**
   - Go to the WAF console and create a new Web ACL.
   - Add a rule to block the IP address:
     - Type: IP match rule.
     - IP Address: Specify the IP to block.
     - Action: Block.

2. **Associate the Web ACL with the ALB:**
   - In the WAF console, associate the Web ACL with your ALB.

3. **Test the Setup:**
   - Verify that requests from the blocked IP address are denied.

---

## Blocking an IP Address – ALB, CloudFront WAF
1. **Set Up CloudFront Distribution:**
   - Go to the CloudFront console and create or select an existing distribution.
   - Ensure the ALB is configured as the origin.

2. **Create a WAF Rule for CloudFront:**
   - In the WAF console, create a Web ACL.
   - Add an IP match condition for the specific IP to block.
   - Set the action to "Block."

3. **Associate the WAF with CloudFront:**
   - Attach the Web ACL to the CloudFront distribution.

4. **Validate the Configuration:**
   - Use the blocked IP address to attempt access and confirm the block is effective.

---

By following these steps, you can effectively block unwanted IP addresses in various AWS setups, ensuring robust security and control over access to your resources.
