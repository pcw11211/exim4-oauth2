# exim4-oauth2

the needed configuration to make exim4 utilize xoauth2 authentication and be able to use gmail for sending out email: 
based on https://developers.google.com/gmail/imap/xoauth2-protocol

1. configure exim4 per your needs
   for sending out only:
   - run dpkg-reconfigure exim4-config
   - mail sent by smarthost; no local mail
   - System mail name: localhost
   - IP-address to listen on for incoming SMTP connections: 127.0.0.1 ; ::1
   - Other destinations for which mail is accepted: localhost
   - Machines to relay mail for: <leave this blank>
   - Setting Outbound Mailbox Destination: smtp.gmail.com::587
   - Keep number of DNS-queries minimal (Dial-on-Demand)? No
   - Split configuration file into small files? Yes
2. you need to get client_id and client secret
  there are a lot of resources on goole how to get client is and secret
  basically you need to create an app and publish it for public (or only for your user)
3. generate refresh token in oauth playground:
  there are a lot of resources on goole how to do this also
  make sure to use your client id and secret in oauth playground
  select "https://mail.google.com/" as scope (you can use sub categories like read-only or send-only scope depending on your needs)
4. authorize your app with desired gmail account to give app api access to your account and to recieve refresh token
5. put get_bearer_tocken.sh script in /etc/exim4 folder
6. set variales in get_bearer_tocken.sh with correct values
   - client id
   - client secret
   - refresh token
   - account email addreess that authorised the ap in step 3
7. edit /etc/exim4/conf.d/auth/30_exim4-config_examples: see repo
8. edit /etc/exim4/passwd.client: see repo
