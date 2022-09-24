# TLS

## Certificates

```sh
# Check the expiration date of the certificate - wildcard
echo | openssl s_client -servername wildcard.google.com -connect google.com:443 2>/dev/null | openssl x509 -noout -issuer -subject -dates

# Check the expiration date of the certificate
echo | openssl s_client -servername google.net -connect google.net:443 2>/dev/null | openssl x509 -noout -issuer -subject -dates

# Check the Common Name (CN) of the certificate
echo | openssl s_client -servername api.sg-form.com -connect google.net:443 2>/dev/null | openssl x509 -noout -subject
```
