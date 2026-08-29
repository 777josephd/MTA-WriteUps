# Snake Keylogger Analysis

Immediately, we see fingerprinting activity from the endpoint querying `checkip.dyndns.org` and again with `reallyfreegeoip.org`.

<img width="1714" height="614" alt="1-Initial" src="https://github.com/user-attachments/assets/3504f098-ae98-44fd-aeab-dd755fed98a7" />

The query responds with the public IP `173[.]166[.]146[.]112`.  
We also note that the IP check is run several times.

<img width="1714" height="768" alt="2-1-FIX-Public-IP" src="https://github.com/user-attachments/assets/d4e43b9b-e47d-4484-ad0f-17715a82cab1" />

Checking Conversations, activity on port 21 and 2 ephemeral ports is noted.

<img width="1714" height="204" alt="5-conversations" src="https://github.com/user-attachments/assets/b3fc7059-d897-4c4e-87b1-5e54478d824a" />

Scrolling through the traffic, we come across cleartext FTP traffic with the user's username and password, along with the server name.

<img width="1714" height="610" alt="6-Plaintext-FTP" src="https://github.com/user-attachments/assets/17e7ae0e-f5be-4b0e-9cca-69f9ec31f9ee" />

Following the stream, we see the credentials and other relevant information, all in cleartext.

<img width="1714" height="794" alt="7-FTP-Data" src="https://github.com/user-attachments/assets/5770eecb-5fcd-47db-944e-5028f0a5a22a" />

We can observe the objects created during the session. Static analysis is beyond the scope of this session.

<img width="1714" height="288" alt="8-FTP-Data-2" src="https://github.com/user-attachments/assets/0fdfb3e5-51ba-4312-be76-e03f8bdaae37" />
