# Generate .csr and .key file

openssl req -new -newkey rsa:2048 -nodes \
  -keyout domain-name.key -out domain-name.csr \
  -config openssl.cnf

# For self signed certificate, generate a .crt

openssl x509 -req -in domain-name.csr -signkey domain-name.key -out domain-name.crt -days 365

