How to Analyse Emails?

Before learning how to conduct an email analysis, you need to know the structure of an email header. Let's quickly review the email header structure.

| Field | Details |
| --- | --- |
| From | The sender's address.|
| To |  The receiver's address, including CC and BCC.
| Date | Timestamp, when the email was sent.
| Subject | The subject of the email.
| Return Path | The return address of the reply, a.k.a. "Reply-To".If you reply to an email, the reply will go to the address mentioned in this field. | 
| Domain Key and DKIM Signatures | Email signatures are provided by email services to identify and authenticate emails.
| SPF |Shows the server that was used to send the email. It will help to understand if the actual server is used to send the email from a specific domain.
|Message-ID	|Unique ID of the email.
|MIME-Version|	Used MIME version. It will help to understand the delivered "non-text" contents and attachments.|
|X-Headers|	The receiver mail providers usually add these fields. Provided info is usually experimental and can be different according to the mail provider.
|X-Received|	Mail servers that the email went through.
|X-Spam Status	|Spam score of the email.
|X-Mailer	| Email client name.

