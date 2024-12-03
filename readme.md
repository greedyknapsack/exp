Here is a detailed note on SMTP along with a diagram that can be rendered in GitHub using Markdown:

### Simple Mail Transfer Protocol (SMTP)

#### Overview
SMTP (Simple Mail Transfer Protocol) is an Internet standard protocol used for the transmission of emails across IP networks. It is a protocol used to send, receive, and relay outgoing mail between email senders and receivers.

#### Key Features
- **Connection-Oriented**: SMTP establishes a connection between the sender and receiver before transmitting the email.
- **Text-Based Protocol**: SMTP commands and responses are text-based, making it easy to read and debug.
- **Push Protocol**: SMTP is a push protocol, meaning it pushes the email from the client to the server.

#### SMTP Process
1. **Client Initiation**: The email client (sender) initiates a connection to the SMTP server.
2. **Handshake**: The client and server perform a handshake to establish a connection.
3. **Mail Transfer**: The client sends the email data to the server using SMTP commands.
4. **Server Response**: The server processes the email and responds with status codes indicating success or failure.
5. **Connection Termination**: The connection is terminated after the email is successfully sent.

#### SMTP Commands
- **HELO/EHLO**: Initiates the conversation between the client and server. EHLO is the extended version of HELO.
- **MAIL FROM**: Specifies the sender's email address.
- **RCPT TO**: Specifies the recipient's email address.
- **DATA**: Indicates the start of the message content.
- **QUIT**: Terminates the SMTP session.
- **RSET**: Resets the current mail transaction.
- **VRFY**: Verifies an email address.
- **EXPN**: Expands a mailing list.
- **HELP**: Provides help information.

#### SMTP Status Codes
- **2xx**: Success (e.g., 250 OK)
- **3xx**: Intermediate (e.g., 354 Start mail input)
- **4xx**: Temporary Failure (e.g., 421 Service not available)
- **5xx**: Permanent Failure (e.g., 550 Requested action not taken)

#### SMTP Ports
- **Port 25**: Default port for SMTP communication.
- **Port 587**: Used for email submission with encryption (STARTTLS).
- **Port 465**: Used for SMTP over SSL (deprecated but still in use).

#### Security
- **STARTTLS**: Upgrades an existing insecure connection to a secure connection using TLS.
- **SMTP Authentication (SMTP AUTH)**: Requires the client to authenticate with the server before sending emails, preventing unauthorized use.

#### Use Cases
- **Sending Emails**: SMTP is primarily used to send emails from a client to a server or between servers.
- **Relaying Emails**: SMTP can relay emails between different email servers.
- **Bulk Email Sending**: SMTP is used by bulk email services to send large volumes of emails.

#### Limitations
- **No Built-in Encryption**: SMTP does not provide built-in encryption, making it susceptible to eavesdropping. Encryption is added using STARTTLS.
- **Spam and Abuse**: SMTP can be exploited for sending spam emails if proper authentication and security measures are not in place.

#### Example SMTP Session
```plaintext
Client: HELO example.com
Server: 250 Hello example.com

Client: MAIL FROM:<sender@example.com>
Server: 250 OK

Client: RCPT TO:<recipient@example.com>
Server: 250 OK

Client: DATA
Server: 354 Start mail input; end with <CRLF>.<CRLF>

Client: Subject: Test Email
Client: This is a test email.
Client: .


Server

: 250 OK

Client: QUIT
Server: 221 Bye
```

#### Diagram
```mermaid
sequenceDiagram
    participant Client
    participant Server

    Client->>Server: HELO example.com
    Server-->>Client: 250 Hello example.com

    Client->>Server: MAIL FROM:<sender@example.com>
    Server-->>Client: 250 OK

    Client->>Server: RCPT TO:<recipient@example.com>
    Server-->>Client: 250 OK

    Client->>Server: DATA
    Server-->>Client: 354 Start mail input; end with <CR><LF>.<CR><LF>

    Client->>Server: Subject: Test Email<br>This is a test email.<br>.
    Server-->>Client: 250 OK

    Client->>Server: QUIT
    Server-->>Client: 221 Bye
```

This diagram illustrates the sequence of commands and responses in a typical SMTP session.
