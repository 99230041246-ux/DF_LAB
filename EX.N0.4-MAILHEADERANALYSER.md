# Ex.No.4   MHA (Mail Header Analyzer)
## Aim :
- The aim is to use a Mail Header Analyzer (MHA) to trace an email's origin and verify its authenticity by examining its header for signs of spoofing.
## Procedure
### Step 1: Get the Email Header
- First, you need to copy the full, raw header from the email.

- Gmail: Open the email, click the three dots (⋮), and select Show original.
<br>
<br>
<img width="1919" height="1014" alt="Screenshot 2025-09-01 152211" src="https://github.com/user-attachments/assets/6c0164e1-ffd1-4e03-b610-2c0d34f26f23" />


<br>
<br>
<img width="1919" height="1025" alt="Screenshot 2025-09-01 152302" src="https://github.com/user-attachments/assets/d8e0e95d-f7e4-4813-ab10-db7edc052a27" />


- Select all the text in the header and copy it.

<br>
<img width="1443" height="910" alt="Screenshot 2025-09-01 152317" src="https://github.com/user-attachments/assets/a7038732-8c47-4062-8636-bb01f05657c7" />

<br>
<br>

### Step 2: Use a Mail Header Analyzer (MHA)
- The easiest way to analyze the header is with an online tool.

- Navigate to a site like MXToolbox Email Header Analyzer.
 <br>
<br>

  <img width="1919" height="913" alt="Screenshot 2025-09-01 152425" src="https://github.com/user-attachments/assets/b0f9c362-16a7-4760-a10a-3e82882f8ca0" />

<br>
<br>

- Paste the entire header you copied into the analysis box.
<br>
<br>

Click the "Analyze" button to get a parsed, easy-to-read report.
<br>
<br>

<img width="1918" height="918" alt="Screenshot 2025-09-01 152444" src="https://github.com/user-attachments/assets/48297971-f5c1-4421-9d71-5f40c600bb4e" />

### Step 3: Analyze The Report
- This is the most critical step. In the analyzer's report, look for the SPF, DKIM, and DMARC results.
### Review the Overall Delivery Summary
- First, look at the high-level summary to get an immediate sense of the email's status.

- Check DMARC Compliance: The report shows the email is DMARC Compliant. This is the most important overall result.

- Check SPF Status: Both SPF Authenticated and SPF Alignment passed. This means the sending server was authorized.

- Check DKIM Status: DKIM Alignment passed, but DKIM Authenticated failed (❌). This is a critical finding and indicates a problem with the email's digital signature.
<br>
<br>
<img width="1893" height="912" alt="Screenshot 2025-09-01 152503" src="https://github.com/user-attachments/assets/58719013-dae2-4a13-bbaa-39a632b80774" />


<br>
<br>

### Investigate the SPF Record and Email Path
- Next, verify why the SPF check passed.

- Examine the SPF Record: The SPF record for the domain is v=spf1 include:mailgun.org ~all. This record explicitly authorizes servers from Mailgun to send emails on its behalf.

- Trace the Relay Information: The delivery path shows the email was sent from m241-136.mailgun.net.

- Conclusion: Since the email came from a Mailgun server, which is authorized in the SPF record, the SPF check passed.
  <br>
  <br>
<img width="1898" height="909" alt="Screenshot 2025-09-01 152523" src="https://github.com/user-attachments/assets/0ed3e1bb-874c-4da9-b5a2-376f8a71f1d2" />

<br>
<br>

### Analyze the DKIM Failure

<br>
<img width="1893" height="907" alt="Screenshot 2025-09-01 152547" src="https://github.com/user-attachments/assets/f2f19dcc-e8d3-4bd4-a204-e4487014f8bf" />
