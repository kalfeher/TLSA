# TLSA
Role to add TLSA records from certificates.

The role expects that certificates are in individual files. Typically this means a file for the server certificate and a separate file for the CA issuing certificate, if desired. Files which combine both certificates should be excluded. If you have an application that requires both server and issuer certificates in a single file, you can configure your ACME client to generate both types.

## Required Variables
`domains`: A list of dictionaries specifying domains and the services they are used for. This are the specific labels for which a service will respond.
~~~yaml
domains:
  - { name: example.com, services: ['postfix', 'dovecot', 'apache'] }
~~~
## Recommended Variables
`cert_root_dir`: The root directory under which all domain subdirectories containing certificates are expected.
~~~yaml
cert_root_dir: "/etc/certificates/"
~~~
`cert_exclude_patterns`: List of patterns to be excluded from TLSA record generation. If your private key is in the same directory as your live certificates, it should be excluded. Fullchain certificates should be excluded with this variable.
~~~yaml

~~~
## Optional Variables
`cert_sub_dir`: Optional subdirectory that certificates are found in beneath the domain directory.
~~~yaml
cert_sub_dir: "certs"
~~~
