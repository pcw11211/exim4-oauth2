# exim4-oauth2

the needed configuration to make exim4 utilize xoauth2 authentication and be able to use gmail for sending out email:

1. you need to get client_id and client secret
  there are a lot of resources on goole how to get client is and secret
  basically you need to create an app and publish it for public (or only for your user)
2. generate refresh token in oauth playground:
  there are a lot of resources on goole how to do this also
  make sure to use your client id and secret in oauth playground
  select "https://mail.google.com/" as scope (you can use sub categories like read-only or send-only scope depending on your needs)
3. authorize your app with desired gmail account to give app api access to your account and to recieve refresh token
