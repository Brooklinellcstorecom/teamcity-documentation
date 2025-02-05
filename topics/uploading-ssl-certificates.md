[//]: # (title: Uploading SSL Certificates)
[//]: # (auxiliary-id: Uploading SSL Certificates)

It is possible to upload an SSL certificate which TeamCity considers trusted when establishing connection by HTTPS or SSL protocols. These can be self-signed certificates or certificates signed by a not well-known certificate authority (CA).

## Adding trusted certificates to TeamCity server

The trusted certificate storage is global for the whole server and affects all server projects.

To add a trusted certificate:
1. Navigate to the Root project __Administration__ area and select the __SSL/HTTPS Certificates__ menu item in the sidebar.
2. Click __Upload certificate__, specify the certificate name and choose a certificate file of one of the __supported formats__: PEM, DER or PKCS#7.
3. Save your changes.

The uploaded certificate will be applied to all the settings on the server.

## Delivering certificates to TeamCity agents

All uploaded certificates will be automatically delivered to all TeamCity agents.

However, sometimes automatically distributing certificates to all agents may not be needed or may be undesirable. Then, you can __manually__ add certificates to a required agent by placing them into the `<[TeamCity Agent Home](agent-home-directory.md)>/conf/trustedCertificates` directory (one file per certificate, certificates in textual form in one of the supported formats mentioned above). Note that this directory is used for storing manually added certificates only; automatically distributed certificates are stored separately, alongside other system files.

This can be useful in the following cases:
* If the user is running the TeamCity server under a non-trusted certificate, you need to place the server certificate into this directory on an agent to establish agent-server connection
* If the user considers their network connection between the server and agents insecure and does not want to transfer sensitive information.