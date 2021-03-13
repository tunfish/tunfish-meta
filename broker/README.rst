    # Create client key and certificate signing request (CSR).
    openssl genrsa -out broker.key 4096
    openssl req -new -key broker.key -out broker.csr -utf8 -batch -subj '/CN=hello.example.org/emailAddress=root@hello.example.org'

    # Request root certificate in PEM format.
    http http://localhost:8000/issuer/RootCA.pem

    # Sign a client certificate.
    cat example.csr | http http://localhost:8000/pki/RootCA/autosign Content-Type:application/x-pem-file