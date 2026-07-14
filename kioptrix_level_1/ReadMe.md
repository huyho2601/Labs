**## Objective**

The purpose of this penetration testing is to strengthen the pentest skill, deepen the understanding, and put all the skills in practice

**## Lab setup**

Download the kioptrix rar file from vulnhub website. Unzip the rar file and run .vmx file on VMWare. There is an issue that even though I changed the network connection to **NAT** in settings, the .vmx file always automatically switched back to **Bridged**

To fix this issue, I opened the .vmx file in text editor and change the associated value of ethernet0.networkName to nat. This helped resolved the problem of network connection.

