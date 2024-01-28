# Locking-down-Vm-with-NSG-in-Azure
![Screenshot 2024-01-28 nsg](https://github.com/AnthonyRams/Locking-down-Vm-with-NSG-in-Azure/assets/156973794/cebb4f20-418f-41ce-9f90-21b0441ab146)


In this project, I am implementing security measures for a Windows Virtual Machine (VM) hosted on Azure by utilizing Network Security Groups (NSGs). The approach involves two key steps:

Step 1 - VM-Level Security with NSG:
- Initially, I implement an NSG (and configure inboud rules) at the VM level to enhance security by restricting Remote Desktop Protocol (RDP) access to port 3389 exclusively from the public IP address of our PC.
- This ensures that only RDP traffic from our specific PC is allowed to reach the Windows VM.


![Screenshot 2024-01-28 1650078](https://github.com/AnthonyRams/Locking-down-Vm-with-NSG-in-Azure/assets/156973794/af51aa4d-51d7-40cc-9e86-2dfc9f4345ea)


Step 2 - Subnet-Level NSG Deployment:
- Next, I deploy an NSG at the subnet level. Since our Windows VM is situated within this subnet, the objective is to control RDP traffic more broadly.
- The subnet-level NSG is configured to only permit RDP traffic from our designated public IP address. This double-layered security measure adds an extra layer of protection, limiting RDP access at both the VM and subnet levels.


  ![Screenshot 2024-01-28 16583758](https://github.com/AnthonyRams/Locking-down-Vm-with-NSG-in-Azure/assets/156973794/dd386bed-4586-41aa-adb3-d3662de7b22d)


- while the Subnet NSG does not have to be in the same resource group, it he helps with management and organizational purposes. However, the NSG needs to be in the same region as our VM.
- Now select the NSG we just created and select "subnet" in the blade on the left.
- Now Select " + Associate".
- Now  Select the Vnet that our VM is deployed and click "OK" at the bottom.

Head over to your VM and under settings in the blade click "networking".

![image](https://github.com/AnthonyRams/Locking-down-Vm-with-NSG-in-Azure/assets/156973794/5071011a-eddd-4e2c-9007-b12c3f7cb5cb)


We should now see the inbound rules for both our VM's NSG and the subnet NSG we created.
- Add inboud rules to our Subnet NSG.
- Lastly, we use the same rules we created for our VM NSG.



### By implementing these NSG configurations, we establish a robust security framework for the Windows VM, safeguarding it against unauthorized RDP access and enhancing the overall security posture within the Azure environment.
