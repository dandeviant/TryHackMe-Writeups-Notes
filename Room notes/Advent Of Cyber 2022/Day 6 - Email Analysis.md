


### How to Analyse Emails?

- Before learning how to conduct an email analysis, you need to know the structure of an email header. Let's quickly review the email header structure.

| Field | Details |
| --- | --- |
| From | The sender's address.|
| To |  The receiver's address, including CC and BCC.
| Date | Timestamp, when the email was sent.
| Subject | The subject of the email.
| Return Path | The return address of the reply, a.k.a. "Reply-To".<br>If you reply to an email, the reply will go to the address mentioned in this field. | 
| Domain Key and DKIM Signatures | Email signatures are provided by email services to identify and authenticate emails.
| SPF |Shows the server that was used to send the email.<br>It will help to understand if the actual server is used to send the email from a specific domain.
|Message-ID	|Unique ID of the email.
|MIME-Version|	Used MIME version. It will help to understand the delivered "non-text" contents and attachments.|
|X-Headers|	The receiver mail providers usually add these fields.<br>Provided info is usually experimental and can be different according to the mail provider.
|X-Received|	Mail servers that the email went through.
|X-Spam Status	|Spam score of the email.
|X-Mailer	| Email client name.

### Important Email Header Fields for Quick Analysis

- Analysing multiple header fields can be confusing at first glance, but starting from the key points will make the analysis process slightly easier. A simple process of email analysis is shown below.

| Questions to Ask / Required Checks | Evaluation |
| --- | --- |
| Do the "From", "To", and "CC" fields contain valid addresses?|Having invalid addresses is a red flag.
| Are the "From" and "To" fields the same?| Having the same sender and recipient is a red flag.
| Are the "From" and "Return-Path" fields the same?| Having different values in these sections is a red flag.
|Was the email sent from the correct server? |Email should have come from the official mail servers of the sender.
|Does the "Message-ID" field exist, and is it valid?| Empty and malformed values are red flags.
|Do the hyperlinks redirect to suspicious/abnormal sites?|Suspicious links and redirections are red flags.
|Do the attachments consist of or contain malware?| Suspicious attachments are a red flag. File hashes marked as suspicious/malicious by sandboxes are a red flag.

- Text editors are helpful in analysis, but there are some tools that can help you to view the email details in a clearer format. In this task, we will use the **"emlAnalyzer"** tool to view the body of the email and analyse the attachments. The emlAnalyzer is a tool designed to parse email headers for a better view and analysis process. The tool is ready to use in the given VM. The tool can show the headers, body, embedded URLs, plaintext and HTML data, and attachments. The sample usage query is explained below.

|Query Details|	Explanation|
|---|---|
|emlAnalyzer	|Main command
|-i 	|File to analyse
|-i |/path-to-file/filename<br>Note: Remember, you can either give a full file path or navigate to the required folder using the "cd" command.
|--header|	Show header
|-u|	Show URLs
|--text|	Show cleartext data
|--extract-all|	Extract all attachments

Sample usage is shown below. Now use the given sample and execute the given command.

```user@ubuntu$ emlAnalyzer -i Urgent\:.eml --header --html -u --text --extract-all
 ==============
 ||  Header  ||
 ==============
X-Pm-Content-Encryption.....end-to-end
X-Pm-Origin.................internal
Subject.....................Urgent: Blue section is down. Switch to the load share plan!
From........................[REDACTED]
Date........................[REDACTED]
Mime-Version................[REDACTED]
Content-Type................[REDACTED]
To..........................[REDACTED]
X-Attached..................[REDACTED]
Message-Id..................[REDACTED]
X-Pm-Spamscore..............[REDACTED]
Received....................[REDACTED]
X-Original-To...............[REDACTED]
Return-Path.................[REDACTED]
Delivered-To................[REDACTED]
 =========================
 ||  URLs in HTML part  ||
 =========================
[+] No URLs found in the html
 =================
 ||  Plaintext  ||
 =================
[+] Email contains no plaintext
 ============
 ||  HTML  ||
 ============
Dear Elves,.......
 =============================
 ||  Attachment Extracting  ||
 =============================
[+] Attachment [1] "Division_of_.......
```

- Additionally, you can use some Open Source Intelligence (OSINT) tools to check email reputation and enrich the findings. Visit the given site below and do a reputation check on the sender address and the address found in the return path.
	-  Tool: https://emailrep.io/
	-  Here, if you find any suspicious URLs and IP addresses, consider using some OSINT tools for further investigation. While we will focus on using Virustotal and InQuest, having similar and alternative services in the analyst toolbox is worthwhile and advantageous.

| Tool | Purpose |
| --- | --- |
| VirusTotal|	A service that provides a cloud-based detection toolset and sandbox environment.
|InQuest|A service provides network and file analysis by using threat analytics.
|IPinfo.io|A service that provides detailed information about an IP address by focusing on geolocation data and service provider.
|Talos Reputation|	An IP reputation check service is provided by Cisco Talos.
|Urlscan.io|	A service that analyses websites by simulating regular user behaviour.
|Browserling|	A browser sandbox is used to test suspicious/malicious links.
| Wannabrowser|	A browser sandbox is used to test suspicious/malicious links.

