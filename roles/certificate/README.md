Certificate
=========

Creates a certificate using Lets Encrypt and Cloudflare DNS.

Role Variables
--------------

cloudflare_api_token: The Cloudflare API token.

cloudflare_account_email: The email address for the account the API token is associated with.

lets_encrypt_account_email: The email to be used for the Lets Encrypt certificate.

domain: The domain requiring a certificate.

certificate_path: The path of which the certificate should be saved.

wildcard_dns: If True a wildcard certificate will be created otherwise a certificate for the specific domain will be
created

common_name: The common name for the certificate, "{{ '*.' + domain if (wildcard_dns) else domain }}" will usually
suffice but you can hard code this.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: 127.0.0.1
      connection: local
      collections:
        - rockprofile.certificates
      tasks:
        - name: Cretificate Renewal
          include_role:
            name: certificate
          vars:
            cloudflare_api_token: cloudflareapitoken
            lets_encrypt_account_email: me@my-domain.com
            cloudflare_account_email: me@my-domain.com
            domain: "my-domain.com"
            certificate_path: ~/certificates
            wildcard_dns: true
            common_name: "{{ '*.' + domain if (wildcard_dns) else domain }}"


License
-------

BSD
