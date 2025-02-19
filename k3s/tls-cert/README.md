# Use openssl.cnf to Generate .csr and .key file

Example using scm-stg-cert:

$ cd scm-stg-cert
$ openssl req -new -newkey rsa:2048 -nodes \
  -keyout scm-stg-cert.key -out scm-stg-cert.csr \
  -config openssl.cnf

# For self signed certificate, generate a .crt file

$ openssl x509 -req -in scm-stg-cert.csr -signkey scm-stg-cert.key -out scm-stg-cert.crt -days 365

# Create secret for targeted namespace

$ kubectl create secret tls scm-stg-cert --cert=scm-stg-cert.crt --key=scm-stg-cert.key  -n {namespace}
