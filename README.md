eyamlwrapper
-----------

##### eyamldecrypt
This script does NOT depend on docker.

```
eyamldecrypt -k|--key <private_key_file> -p|--pub <pkcs_public_key_file> -d|--directory <dir-with-eyml-files> -q|--quiet -qq|--silent
# Environment variables has priority over options
  EYAMLDECRYPT_PRIVATE_KEY      PKCS7 private key            export EYAMLDECRYPT_PRIVATE_KEY=\$(cat ./keys/private_key.pkcs7.pem)
  EYAMLDECRYPT_PUBLIC_KEY       PKCS7 public key             export EYAMLDECRYPT_PUBLIC_KEY=\$(cat ./keys/public_key.pkcs7.pem)
  EYAMLDECRYPT_CONF_DIR         Directory of eyml files      export EYAMLDECRYPT_CONF_DIR=./application/configs/
```

##### eyamlencrypt
This script DOES depend on docker. See [halberom/docker_hiera-eyaml](https://hub.docker.com/r/halberom/hiera-eyaml/) for more details.

It can encrypt a value..
```
$ eyamlencrypt myvalue
string: ENC[PKCS7,MIIBeQYJKoZIhvcNAQcDoIIBajCCAWYCAQAxggEhMIIBHQIBADAFMAACAQEwDQYJKoZIhvcNAQEBBQAEggEAcn+S4u5wTIAZ6vvQK/8onrrqq1oRuYrwNkn9FUNrB/7FqiKzDag0hdi42C+h48+w/GPqJUlzhOne5wzm7y1q7MoYdIHQYikAyVKNfnbGz8x6i6FHZJHlQMMG3q/N/DS2TIatcgjLT8tWoQuuT97yL/6ewsOyoD9yfQG7JBbu014Ws6YaiUmfPjpuBnxFBgqqCsg6OUQ4DIut8SXVa0737IagW+u1SRMBTcDUoI/Muccd9eJHToHFXt1iRNoAa1rvt8qb21T0agGbekKAlufpncQw/ZMCOH1XBBaPfhu6JaxHaE8p7cO2WRcCzJBYfgn1XXCGt6xfHjDdoca99+cglTA8BgkqhkiG9w0BBwEwHQYJYIZIAWUDBAEqBBD5/KkHuQw2MaSGnDAoUuG8gBBcmbtTMNZba1BlMjGMod3n]
```

.. or a file
```
$ eyamlencrypt /myfile
>> Encrypting file '/myfile'
string: ENC[PKCS7,MIIBeQYJKoZIhvcNAQcDoIIBajCCAWYCAQAxggEhMIIBHQIBADAFMAACAQEwDQYJKoZIhvcNAQEBBQAEggEAkswuInY4FyrDbVezK684v0CGe/dOT+cJbcJAHcbi+EcRfCbVKJYXJbtf80/mkBNnG3SpYFgcWfNZEmGRlBJAxtFeUDm0Ax7sS7J/l0YrWh/NF4WOxOBmJR+/EgCmwIiuYjHseCr50N6iwrgWXDIxpXbFQ8Y6NuFSe/EYPjwLpYTHDlKdwwNPajFroVSDeknZyqctM4MZKT99Vnlv0ztbt4/2zi0K2Kx7V8IQLA3rPPWlpN+pHGEzUlPymTenYMyCRzYJSLpOdU4eGFkA2bYOHADImILYZNv+tBQgFXKInHYSbh/FXFuzdEh3tTjDcgG0dAmZraKGh2LnwzOZ/tQy2zA8BgkqhkiG9w0BBwEwHQYJYIZIAWUDBAEqBBADsDSLpzvI13vOBRLr6VvhgBASOZRhXgJBcPLWMg5gO8AO]
```
