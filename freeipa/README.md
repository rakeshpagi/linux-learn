### 1 GEN PRIV KEY
- openssl genrsa -out test.pem 2048

### 2 GEN CSR
- openssl req -key test.key -new -subj '/CN=test/O=CORP.LOCAL'  -out test.csr


### Generate p12
- openssl pkcs12 -export -in test-cert.pem -inkey test.key -out  test.p12 -name "test@CORP.LOCAL"  -passout pass:

### Test P12 
- openssl pkcs12 -info -in test.p12 -passin pass: -noenc

### 3 KINIT GET TGT in (Mac)
- /opt/homebrew/Cellar/krb5/1.21.3/bin/kinit -X X509_user_identity='PKCS12:test.p12' -X X509_anchors='FILE:/Users/${USERID}/learn/rhel/openssl/ipa.pem' -V test@CORP.LOCAL