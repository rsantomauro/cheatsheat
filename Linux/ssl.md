# SSL

All info refering to certificates and configs.

## TLS

To validate TLS and SSL configs:

```bash
openssl ciphers -v | awk '{print $2}' | sort | uniq
```

To make some free ssl repot:

- [SSLLabs](https://www.ssllabs.com/ssltest/)
