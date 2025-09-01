#   Ex.No.3   Wireshark – Network Packet Capture and Analysis Tool


## Procedure: Capturing Plaintext Passwords

### Step 1: Start Capturing Packets
- First, open Wireshark. You will see a list of all available network interfaces (e.g., "Wi-Fi," "Ethernet").


- Select the interface your computer is using to connect to the internet (in this case, Wi-Fi).

  <br>
   <br>
  <img width="1919" height="1018" alt="Screenshot 2025-09-01 151711" src="https://github.com/user-attachments/assets/d450796d-1f1a-4606-abaf-76f876170a4c" />


  </p>
  <br>
  <br>

- Click the blue shark fin icon 🦈 in the top-left corner to start the capture. Wireshark will immediately begin capturing all traffic passing through that interface.
 <br>
   <br>
  <img width="1916" height="1023" alt="Screenshot 2025-09-01 151728" src="https://github.com/user-attachments/assets/5beb2254-31ca-49ab-97a9-475f92445a48" />

 </p>
  <br>
  <br>

  ### Step 2: Generate Login Traffic
  - Open a web browser and navigate to http://testphp.vulnweb.com/login.php.

- Enter any dummy credentials. For this example, we'll use:

   Username: testuser

   Password: password123

- Click the login button. The login will fail, but the data has already been sent across the network.

 <br>
   <br>
  <img width="1919" height="1020" alt="Screenshot 2025-09-01 151816" src="https://github.com/user-attachments/assets/60627b17-bf76-4501-9c43-4160426fdc91" />

 </p>
  
  
### step 3: Stop Capture and Filter Traffic

- Return to Wireshark and click the Stop button (the red square).

- In the display filter bar, you need to find the packet containing the login data. Since the form data was sent to the server, we will look for an HTTP POST request.

- Apply the following filter to find the exact packet and press Enter:

 <br>
   <br>
  <img width="1919" height="1023" alt="Screenshot 2025-09-01 151932" src="https://github.com/user-attachments/assets/9a5f0b8c-8670-4d34-94ef-2055375bd444" />

 </p>
  <br>
  <br>

### step 4: Inspect the Packet to Find Credentials 

- In the filtered packet list, you should see a packet with information like "POST /userinfo.php". Select this packet.

- In the Packet Details pane below the list, expand the following sections:

Hypertext Transfer Protocol

HTML Form URL Encoded

- Inside the "HTML Form URL Encoded" section, you will see the credentials you entered in plaintext.

 <br>
   <br>
  <img width="1919" height="883" alt="Screenshot 2025-09-01 152044" src="https://github.com/user-attachments/assets/c0f7abb1-7c4a-4cf2-a6fa-a156e280c0ce" />

 </p>
  <br>
  <br>

---

## Result
The experiment successfully intercepts the login credentials in a human-readable format. The analysis of the captured POST packet reveals the plaintext data that was transmitted over the network:

This result confirms the inherent security flaw of the HTTP protocol. Any sensitive data sent over HTTP is transmitted openly, making it trivial to intercept.
