# Generate .csr and .key file

$ openssl req -new -newkey rsa:2048 -nodes \
  -keyout scm-stg.key -out scm-stg.csr \
  -config openssl.cnf

# For self signed certificate, generate a .crt

$ openssl x509 -req -in scm-stg.csr -signkey scm-stg.key -out scm-stg.crt -days 365

# Create secret for targeted namespace

$ kubectl create secret tls scm-stg-cert --cert=scm-stg.crt --key=scm-stg.key  -n {namespace}
