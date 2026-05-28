

<img width="860" height="331" alt="image" src="https://github.com/user-attachments/assets/38e26bab-734f-4239-80f5-396031b0cd0a" />
<img width="833" height="414" alt="image" src="https://github.com/user-attachments/assets/e2fc9305-c691-43bd-8e97-c0c6a90a3e4c" />
<img width="846" height="280" alt="image" src="https://github.com/user-attachments/assets/ea1fcc0a-3faf-4c6a-9038-1c089e44eff3" />
<img width="804" height="302" alt="image" src="https://github.com/user-attachments/assets/1951a882-83a3-4966-9b9f-44d1475baa29" />



EventID 4624


Logon Type = 3, Network,  Remote,	could be SMB, PsExec, WMI, lateral movement

Logon Type = 10, Remote Interactive (RDP), Remote, Full RDP session
Recall that every RDP login comprises two 4624 events. You need the one with Logon Type 3 to potentially identify the hostname of the attacker.


RDP Brute Force
1. Open Security logs and filter for the failed logins (event ID 4625)
2. Filter for logon types 3 and 10, meaning remote logons
3. Filter for logins from external IPs (use "Source IP" field)
4. Recall that every RDP login comprises two 4624 events. You need the one with Logon Type 3 to potentially identify the hostname of the attacker.

Initial Access via RDP
1. Continue with the list from the previous step
2. Switch the event ID filter to 4624 (successful logins)
3. Check the account under which the logon was made

4	Further Malicious Actions
1. Continue with the list from the previous step
2. Filter for logon type 10, indicating interactive RDP login
3. Copy the "Logon ID" field from the logon event
4. Open Sysmon logs and search events with the same "Logon ID"
5. You will see all processes started by the threat actor via RDP
