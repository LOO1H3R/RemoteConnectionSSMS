### How to connect to connect to a remote SQL Server instance from AWS using SQL Server Management Studio (SSMS)

## AWS Dashboard
1. From the AWS console, go to the EC2 dashboard and select the instance you want to connect to.

2. Click on the "Security" tab and then click on the "Security Groups" link.

3. Click on the security group that is associated with the instance you want to connect to.

4. Click on the "Inbound rules" tab and then click on the "Edit inbound rules" button.

5. Click on the "Add rule" button and then select "SQL Server" from the "Type" dropdown menu.

6. In the "Source" field, enter the IP address of the machine you want to connect from.

7. Do it for IP4 and IP6

8. Click on the "Save rules" button.

## Instance
9. Connect to the instance and search SQL SERVER 2022 Configuration Manager.

10. Click on SQL Server Network Configuration and then click on Protocols for [instance name] in this case is DEVELOPER.

11. Right-click on TCP/IP and select "Enable".

12. Right-click on TCP/IP and select "Properties".

13. Click on the "IP Addresses" tab and then scroll down to the "IPAll" section.

14. In the "TCP Port" field, enter the port number [1433] that you want to use for the connection.

15. Click on the "OK" button.

16. Restart the SQL Server service in the SQL Server Configuration Manager/SQL Server Services.

17. Go to Windows Defender Firewall with Advanced Security and click on Inbound Rules.

18. Click on New Rule and select Port.

19. Click on TCP and enter the port number [1433] that you want to use for the connection.

20. Click on Allow the connection and then click on Next.

21. Click on the "Domain", "Private", and "Public" checkboxes and then click on Next.

22. Enter a name for the rule and then click on Finish.

## From your own machine

23. Open SQL Server Management Studio (SSMS) and click on the "Connect" button.

24. In the "Server name" field, enter the public IP address [^1] or the public DNS provided by AWS of the instance you want to connect to, followed by a comma and the port number [1433] that you specified in the "IPAll" section of the SQL Server Configuration Manager.

```plaintext
[Public IP address],[Port number]\[Instance name]

for example:
123.456.789.012,1433\DEVELOPER
```
25. In the "Authentication" field, select "SQL Server Authentication".

26. In the "Login" field, enter the username and the password of the SQL Server instance.

27. Click on the "Connect" button.

Now you should be connected to the remote SQL Server instance.

[^1]: By default, AWS assign dynamic public IP addresses to instances. If you stop and start the instance, the public IP address changes. To ensure that you always have the same public IP address, you can associate an Elastic IP address with the instance.
