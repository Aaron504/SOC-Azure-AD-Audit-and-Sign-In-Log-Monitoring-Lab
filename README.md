# SOC Azure AD Audit and Sign In Log Monitoring Lab (Tenant level)
<p align="center">

  ![image](https://github.com/user-attachments/assets/3cea825c-67d6-47d1-b63a-14dc0dc5f9b6)

</p>

In this lab, I configured logging for Azure Active Directory (AAD), enabling the ingestion of Audit and Sign-In logs into a Log Analytics Workspace. I performed tasks such as creating diagnostic settings, generating logs by creating and deleting a dummy user, and assigning Global Administrator roles. As an attacker, I simulated a brute force attack by generating multiple failed logins. Using KQL queries, I analyzed both the Audit and Sign-In logs, identifying role changes and failed login attempts. This lab demonstrates my ability to monitor and investigate AAD activities for potential security threats.



<h2>Environments and Technologies Used</h2>

- Log Analytics Workspaces
- Active Directory Domain Services


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 - Create Diagnostic Settings to ingest Azure AD Logs
- Step 2 - Check Log Analytics Workspace that the tables have been created: “AuditLogs” “SigninLogs”
- Step 3 - Create a dummy user, username “dummy_user”
- Step 4 - Log in with it once (incognito window)
- Step 5 - Assign dummy_user the Role of Global Administrator
- Step 6 - Rebuild/understand this query
- Step 7 - Simulate Brute Force Attack against Azure Active Directory (aka Microsoft Entra ID)




<h2>Deployment and Configuration Steps</h2>

- Create Diagnostic Settings to ingest Azure AD Logs
- Enable Audit Logs and Signin Logs for Azure AD
![Screenshot 2024-10-10 170922](https://github.com/user-attachments/assets/94d87817-353c-4383-83d2-56b223da9126)

- Check Log Analytics Workspace that the tables have been created: “AuditLogs” “SigninLogs”
![Screenshot 2024-10-10 173227](https://github.com/user-attachments/assets/8c03f9f5-b518-477a-942f-0722e854468e)

- Create a dummy user, username “dummy_user”
![Screenshot 2024-10-10 171731](https://github.com/user-attachments/assets/2f842268-875e-4e72-b3d4-f8d5c88f82c3)

- Log in with it once (incognito window)
![Screenshot 2024-10-10 172111](https://github.com/user-attachments/assets/ef4a9357-8522-44e1-865b-78c27f269110)

- Assign dummy_user the Role of Global Administrator
![Screenshot 2024-10-10 172745](https://github.com/user-attachments/assets/bcaa0b02-8d76-4579-bf88-d86fe1e0879d)

- Observe Audit Logs logs in Log Analytics Workspace
![Screenshot 2024-10-10 173629](https://github.com/user-attachments/assets/b9900133-cf25-4d4e-a004-6994bc96ef2b)

- Rebuild/understand this query
- This query is designed to track successful role assignments in Azure Active Directory (AAD), focusing on the critical roles of Global Administrator and Company Administrator. The query filters audit logs to identify when a user is added to one of these roles, ensuring the action was successful. It provides detailed information, such as the time of the event, the specific role assigned, and the target resources involved. This query is essential for auditing and maintaining security within an organization by monitoring elevated privileges granted to users.
![Screenshot 2024-10-10 174355](https://github.com/user-attachments/assets/df7891d2-7f42-4a8a-ad6e-5656c9067bc0)

- Attacker Mode (pretend you are an attacker):
- Simulate Brute Force Attack against Azure Active Directory (aka Microsoft Entra ID)
- Create the “attacker” user if not exists already
- Produce 10-11 failed Logins with the portal
![Screenshot 2024-10-10 180256](https://github.com/user-attachments/assets/87f62943-6d45-4c63-bafd-f0bd558d5b2b)
![Screenshot 2024-10-10 181347](https://github.com/user-attachments/assets/7d24f9a1-a917-47fd-b076-64d0393bdfbc)
![Screenshot 2024-10-10 181934](https://github.com/user-attachments/assets/a9df47b6-4de4-4887-a2de-ffc0f77129a0)

- Rebuild/understand this query:
- This query analyzes failed sign-in attempts in Azure Active Directory (AAD) by filtering the SigninLogs for events where the result indicates an "Invalid username or password" error. It retrieves detailed location information by parsing the LocationDetails field, which includes the city, state, country, and geographical coordinates (latitude and longitude) of the failed sign-in attempt. The query also projects key details such as the time of the event, user principal name, application used, and IP address. This query is useful for identifying patterns in failed login attempts and potential unauthorized access attempts based on geographical data, aiding in security monitoring and incident response.

![Screenshot 2024-10-10 182415](https://github.com/user-attachments/assets/e42b6152-75d6-4d8d-936f-f5fe6e596d84)














