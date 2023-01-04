


### How to Analyse Emails?

Before learning how to conduct an email analysis, you need to know the structure of an email header. Let's quickly review the email header structure.

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

Analysing multiple header fields can be confusing at first glance, but starting from the key points will make the analysis process slightly easier. A simple process of email analysis is shown below.

| Questions to Ask / Required Checks | Evaluation |
| --- | --- |
| Do the "From", "To", and "CC" fields contain valid addresses?|Having invalid addresses is a red flag.
| Are the "From" and "To" fields the same?| Having the same sender and recipient is a red flag.
| Are the "From" and "Return-Path" fields the same?| Having different values in these sections is a red flag.
|Was the email sent from the correct server? |Email should have come from the official mail servers of the sender.
|Does the "Message-ID" field exist, and is it valid?| Empty and malformed values are red flags.
|Do the hyperlinks redirect to suspicious/abnormal sites?|Suspicious links and redirections are red flags.
|Do the attachments consist of or contain malware?| Suspicious attachments are a red flag. File hashes marked as suspicious/malicious by sandboxes are a red flag.

Text editors are helpful in analysis, but there are some tools that can help you to view the email details in a clearer format. In this task, we will use the **"emlAnalyzer"** tool to view the body of the email and analyse the attachments. The emlAnalyzer is a tool designed to parse email headers for a better view and analysis process. The tool is ready to use in the given VM. The tool can show the headers, body, embedded URLs, plaintext and HTML data, and attachments. The sample usage query is explained below.