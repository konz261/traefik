---
title: "Traefik PassTLSClientCert Documentation"
description: "In Traefik Proxy's HTTP middleware, the PassTLSClientCert adds selected data from passed client TLS certificates to headers. Read the technical documentation."
---

The `passTLSClientCert` middleware adds the selected data from the passed client TLS certificate to a header.

## Configuration Examples

Pass the pem in the `X-Forwarded-Tls-Client-Cert` header:

```yaml tab="Structured (YAML)"
# Pass the pem in the `X-Forwarded-Tls-Client-Cert` header.
http:
  middlewares:
    test-passtlsclientcert:
      passTLSClientCert:
        pem: true
```

```toml tab="Structured (TOML)"
# Pass the pem in the `X-Forwarded-Tls-Client-Cert` header.
[http.middlewares]
  [http.middlewares.test-passtlsclientcert.passTLSClientCert]
    pem = true
```

```yaml tab="Labels"
# Pass the pem in the `X-Forwarded-Tls-Client-Cert` header.
labels:
  - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.pem=true"
```

```json tab="Tags"
// Pass the pem in the `X-Forwarded-Tls-Client-Cert` header
{
  "Tags": [
    "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.pem=true"
  ]
}
```

```yaml tab="Kubernetes"
apiVersion: traefik.io/v1alpha1
kind: Middleware
metadata:
  name: test-passtlsclientcert
spec:
  passTLSClientCert:
    pem: true
```

??? example "Pass the pem in the `X-Forwarded-Tls-Client-Cert` header"

    ```yaml tab="Structured (YAML)"
    # Pass all the available info in the `X-Forwarded-Tls-Client-Cert-Info` header
    http:
      middlewares:
        test-passtlsclientcert:
          passTLSClientCert:
            info:
              notAfter: true
              notBefore: true
              sans: true
              subject:
                country: true
                province: true
                locality: true
                organization: true
                organizationalUnit: true
                commonName: true
                serialNumber: true
                domainComponent: true
              issuer:
                country: true
                province: true
                locality: true
                organization: true
                commonName: true
                serialNumber: true
                domainComponent: true
    ```

    ```toml tab="Structured (TOML)"
    # Pass all the available info in the `X-Forwarded-Tls-Client-Cert-Info` header
    [http.middlewares]
      [http.middlewares.test-passtlsclientcert.passTLSClientCert]
        [http.middlewares.test-passtlsclientcert.passTLSClientCert.info]
          notAfter = true
          notBefore = true
          sans = true
          [http.middlewares.test-passtlsclientcert.passTLSClientCert.info.subject]
            country = true
            province = true
            locality = true
            organization = true
            organizationalUnit = true
            commonName = true
            serialNumber = true
            domainComponent = true
          [http.middlewares.test-passtlsclientcert.passTLSClientCert.info.issuer]
            country = true
            province = true
            locality = true
            organization = true
            commonName = true
            serialNumber = true
            domainComponent = true
    ```

    ```yaml tab="Labels"
    # Pass all the available info in the `X-Forwarded-Tls-Client-Cert-Info` header
    labels:
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.notafter=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.notbefore=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.sans=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.serialnumber=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.commonname=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.country=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.domaincomponent=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.locality=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.organization=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.organizationalunit=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.province=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.serialnumber=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.commonname=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.country=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.domaincomponent=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.locality=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.organization=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.province=true"
      - "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.serialnumber=true"
    ```

    ```json tab="Tags"
    // Pass all the available info in the `X-Forwarded-Tls-Client-Cert-Info` header
    {
      //...
      "Tags" : [
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.notafter=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.notbefore=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.sans=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.commonname=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.country=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.domaincomponent=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.locality=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.organization=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.organizationalunit=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.province=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.subject.serialnumber=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.commonname=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.country=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.domaincomponent=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.locality=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.organization=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.province=true",
        "traefik.http.middlewares.test-passtlsclientcert.passtlsclientcert.info.issuer.serialnumber=true"
      ]
    }
    ```

    ```yaml tab="Kubernetes"
    # Pass all the available info in the `X-Forwarded-Tls-Client-Cert-Info` header
    apiVersion: traefik.io/v1alpha1
    kind: Middleware
    metadata:
      name: test-passtlsclientcert
    spec:
      passTLSClientCert:
        info:
          notAfter: true
          notBefore: true
          sans: true
          subject:
            country: true
            province: true
            locality: true
            organization: true
            organizationalUnit: true
            commonName: true
            serialNumber: true
            domainComponent: true
          issuer:
            country: true
            province: true
            locality: true
            organization: true
            commonName: true
            serialNumber: true
            domainComponent: true
    ```

## General Information

`passTLSClientCert` can add two headers to the request:

- `X-Forwarded-Tls-Client-Cert` that contains the pem.
- `X-Forwarded-Tls-Client-Cert-Info` that contains all the selected certificate information in an escaped string.

!!! info

    - `X-Forwarded-Tls-Client-Cert-Info` header value is a string that has been escaped in order to be a valid URL query.
    - These options only work accordingly to the MutualTLS configuration. i.e, only the certificates that match the `clientAuth.clientAuthType` policy are passed.

??? example "Example of a complete certificate and explaining each of the middleware options"

    ```txt
    Certificate:
        Data:
            Version: 3 (0x2)
            Serial Number: 1 (0x1)
            Signature Algorithm: sha1WithRSAEncryption
            Issuer: DC=org, DC=cheese, O=Cheese, O=Cheese 2, OU=Simple Signing Section, OU=Simple Signing Section 2, CN=Simple Signing CA, CN=Simple Signing CA 2, C=FR, C=US, L=TOULOUSE, L=LYON, ST=Signing State, ST=Signing State 2/emailAddress=simple@signing.com/emailAddress=simple2@signing.com
            Validity
                Not Before: Dec  6 11:10:16 2018 GMT
                Not After : Dec  5 11:10:16 2020 GMT
            Subject: DC=org, DC=cheese, O=Cheese, O=Cheese 2, OU=Simple Signing Section, OU=Simple Signing Section 2, CN=*.example.org, CN=*.example.com, C=FR, C=US, L=TOULOUSE, L=LYON, ST=Cheese org state, ST=Cheese com statemailAddress=cert@example.org/emailAddress=cert@sexample.com
            Subject Public Key Info:
                Public Key Algorithm: rsaEncryption
                    RSA Public-Key: (2048 bit)
                    Modulus:
                        00:de:77:fa:8d:03:70:30:39:dd:51:1b:cc:60:db:
                        a9:5a:13:b1:af:fe:2c:c6:38:9b:88:0a:0f:8e:d9:
                        1b:a1:1d:af:0d:66:e4:13:5b:bc:5d:36:92:d7:5e:
                        d0:fa:88:29:d3:78:e1:81:de:98:b2:a9:22:3f:bf:
                        8a:af:12:92:63:d4:a9:c3:f2:e4:7e:d2:dc:a2:c5:
                        39:1c:7a:eb:d7:12:70:63:2e:41:47:e0:f0:08:e8:
                        dc:be:09:01:ec:28:09:af:35:d7:79:9c:50:35:d1:
                        6b:e5:87:7b:34:f6:d2:31:65:1d:18:42:69:6c:04:
                        11:83:fe:44:ae:90:92:2d:0b:75:39:57:62:e6:17:
                        2f:47:2b:c7:53:dd:10:2d:c9:e3:06:13:d2:b9:ba:
                        63:2e:3c:7d:83:6b:d6:89:c9:cc:9d:4d:bf:9f:e8:
                        a3:7b:da:c8:99:2b:ba:66:d6:8e:f8:41:41:a0:c9:
                        d0:5e:c8:11:a4:55:4a:93:83:87:63:04:63:41:9c:
                        fb:68:04:67:c2:71:2f:f2:65:1d:02:5d:15:db:2c:
                        d9:04:69:85:c2:7d:0d:ea:3b:ac:85:f8:d4:8f:0f:
                        c5:70:b2:45:e1:ec:b2:54:0b:e9:f7:82:b4:9b:1b:
                        2d:b9:25:d4:ab:ca:8f:5b:44:3e:15:dd:b8:7f:b7:
                        ee:f9
                    Exponent: 65537 (0x10001)
            X509v3 extensions:
                X509v3 Key Usage: critical
                    Digital Signature, Key Encipherment
                X509v3 Basic Constraints:
                    CA:FALSE
                X509v3 Extended Key Usage:
                    TLS Web Server Authentication, TLS Web Client Authentication
                X509v3 Subject Key Identifier:
                    94:BA:73:78:A2:87:FB:58:28:28:CF:98:3B:C2:45:70:16:6E:29:2F
                X509v3 Authority Key Identifier:
                    keyid:1E:52:A2:E8:54:D5:37:EB:D5:A8:1D:E4:C2:04:1D:37:E2:F7:70:03

                X509v3 Subject Alternative Name:
                    DNS:*.example.org, DNS:*.example.net, DNS:*.example.com, IP Address:10.0.1.0, IP Address:10.0.1.2, email:test@example.org, email:test@example.net
        Signature Algorithm: sha1WithRSAEncryption
            76:6b:05:b0:0e:34:11:b1:83:99:91:dc:ae:1b:e2:08:15:8b:
            16:b2:9b:27:1c:02:ac:b5:df:1b:d0:d0:75:a4:2b:2c:5c:65:
            ed:99:ab:f7:cd:fe:38:3f:c3:9a:22:31:1b:ac:8c:1c:c2:f9:
            5d:d4:75:7a:2e:72:c7:85:a9:04:af:9f:2a:cc:d3:96:75:f0:
            8e:c7:c6:76:48:ac:45:a4:b9:02:1e:2f:c0:15:c4:07:08:92:
            cb:27:50:67:a1:c8:05:c5:3a:b3:a6:48:be:eb:d5:59:ab:a2:
            1b:95:30:71:13:5b:0a:9a:73:3b:60:cc:10:d0:6a:c7:e5:d7:
            8b:2f:f9:2e:98:f2:ff:81:14:24:09:e3:4b:55:57:09:1a:22:
            74:f1:f6:40:13:31:43:89:71:0a:96:1a:05:82:1f:83:3a:87:
            9b:17:25:ef:5a:55:f2:2d:cd:0d:4d:e4:81:58:b6:e3:8d:09:
            62:9a:0c:bd:e4:e5:5c:f0:95:da:cb:c7:34:2c:34:5f:6d:fc:
            60:7b:12:5b:86:fd:df:21:89:3b:48:08:30:bf:67:ff:8c:e6:
            9b:53:cc:87:36:47:70:40:3b:d9:90:2a:d2:d2:82:c6:9c:f5:
            d1:d8:e0:e6:fd:aa:2f:95:7e:39:ac:fc:4e:d4:ce:65:b3:ec:
            c6:98:8a:31
    -----BEGIN CERTIFICATE-----
    MIIGWjCCBUKgAwIBAgIBATANBgkqhkiG9w0BAQUFADCCAYQxEzARBgoJkiaJk/Is
    ZAEZFgNvcmcxFjAUBgoJkiaJk/IsZAEZFgZjaGVlc2UxDzANBgNVBAoMBkNoZWVz
    ZTERMA8GA1UECgwIQ2hlZXNlIDIxHzAdBgNVBAsMFlNpbXBsZSBTaWduaW5nIFNl
    Y3Rpb24xITAfBgNVBAsMGFNpbXBsZSBTaWduaW5nIFNlY3Rpb24gMjEaMBgGA1UE
    AwwRU2ltcGxlIFNpZ25pbmcgQ0ExHDAaBgNVBAMME1NpbXBsZSBTaWduaW5nIENB
    IDIxCzAJBgNVBAYTAkZSMQswCQYDVQQGEwJVUzERMA8GA1UEBwwIVE9VTE9VU0Ux
    DTALBgNVBAcMBExZT04xFjAUBgNVBAgMDVNpZ25pbmcgU3RhdGUxGDAWBgNVBAgM
    D1NpZ25pbmcgU3RhdGUgMjEhMB8GCSqGSIb3DQEJARYSc2ltcGxlQHNpZ25pbmcu
    Y29tMSIwIAYJKoZIhvcNAQkBFhNzaW1wbGUyQHNpZ25pbmcuY29tMB4XDTE4MTIw
    NjExMTAxNloXDTIwMTIwNTExMTAxNlowggF2MRMwEQYKCZImiZPyLGQBGRYDb3Jn
    MRYwFAYKCZImiZPyLGQBGRYGY2hlZXNlMQ8wDQYDVQQKDAZDaGVlc2UxETAPBgNV
    BAoMCENoZWVzZSAyMR8wHQYDVQQLDBZTaW1wbGUgU2lnbmluZyBTZWN0aW9uMSEw
    HwYDVQQLDBhTaW1wbGUgU2lnbmluZyBTZWN0aW9uIDIxFTATBgNVBAMMDCouY2hl
    ZXNlLm9yZzEVMBMGA1UEAwwMKi5jaGVlc2UuY29tMQswCQYDVQQGEwJGUjELMAkG
    A1UEBhMCVVMxETAPBgNVBAcMCFRPVUxPVVNFMQ0wCwYDVQQHDARMWU9OMRkwFwYD
    VQQIDBBDaGVlc2Ugb3JnIHN0YXRlMRkwFwYDVQQIDBBDaGVlc2UgY29tIHN0YXRl
    MR4wHAYJKoZIhvcNAQkBFg9jZXJ0QGNoZWVzZS5vcmcxHzAdBgkqhkiG9w0BCQEW
    EGNlcnRAc2NoZWVzZS5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIB
    AQDed/qNA3AwOd1RG8xg26laE7Gv/izGOJuICg+O2RuhHa8NZuQTW7xdNpLXXtD6
    iCnTeOGB3piyqSI/v4qvEpJj1KnD8uR+0tyixTkceuvXEnBjLkFH4PAI6Ny+CQHs
    KAmvNdd5nFA10Wvlh3s09tIxZR0YQmlsBBGD/kSukJItC3U5V2LmFy9HK8dT3RAt
    yeMGE9K5umMuPH2Da9aJycydTb+f6KN72siZK7pm1o74QUGgydBeyBGkVUqTg4dj
    BGNBnPtoBGfCcS/yZR0CXRXbLNkEaYXCfQ3qO6yF+NSPD8VwskXh7LJUC+n3grSb
    Gy25JdSryo9bRD4V3bh/t+75AgMBAAGjgeAwgd0wDgYDVR0PAQH/BAQDAgWgMAkG
    A1UdEwQCMAAwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMB0GA1UdDgQW
    BBSUunN4oof7WCgoz5g7wkVwFm4pLzAfBgNVHSMEGDAWgBQeUqLoVNU369WoHeTC
    BB034vdwAzBhBgNVHREEWjBYggwqLmNoZWVzZS5vcmeCDCouY2hlZXNlLm5ldIIM
    Ki5jaGVlc2UuY29thwQKAAEAhwQKAAECgQ90ZXN0QGNoZWVzZS5vcmeBD3Rlc3RA
    Y2hlZXNlLm5ldDANBgkqhkiG9w0BAQUFAAOCAQEAdmsFsA40EbGDmZHcrhviCBWL
    FrKbJxwCrLXfG9DQdaQrLFxl7Zmr983+OD/DmiIxG6yMHML5XdR1ei5yx4WpBK+f
    KszTlnXwjsfGdkisRaS5Ah4vwBXEBwiSyydQZ6HIBcU6s6ZIvuvVWauiG5UwcRNb
    CppzO2DMENBqx+XXiy/5Lpjy/4EUJAnjS1VXCRoidPH2QBMxQ4lxCpYaBYIfgzqH
    mxcl71pV8i3NDU3kgVi2440JYpoMveTlXPCV2svHNCw0X238YHsSW4b93yGJO0gI
    -----END CERTIFICATE-----
    ```

## Configuration Options

| Field      | Description        | Default | Required |
|:-----------|:------------------------------------------------------------|:--------|:---------|
| `pem` | Fills the `X-Forwarded-Tls-Client-Cert` header with the certificate information.<br /> More information [here](#pem). | false      | No      |
| `info.serialNumber` | Add the `Serial Number` of the certificate.<br /> More information about `info` [here](#info). | false | No |
| `info.notAfter` | Add the `Not After` information from the `Validity` part. <br /> More information about `info` [here](#info). | false | No |
| `info.notBefore` | Add the `Not Before` information from the `Validity` part. <br />More information about `info` [here](#info). | false      | No      |
| `info.sans` | Add the `Subject Alternative Name` information from the `Subject Alternative Name` part. <br /> More information about `info` [here](#info). | false      | No      |
| `info.subject` | The `info.subject` selects the specific client certificate subject details you want to add to the `X-Forwarded-Tls-Client-Cert-Info` header. <br />More information about `info` [here](#info). | false      | No      |
| `info.subject.country` | Add the `country` information into the subject.<br /> The data is taken from the subject part with the `C` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.subject.province` | Add the `province` information into the subject.<br /> The data is taken from the subject part with the `ST` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.subject.locality` | Add the `locality` information into the subject.<br /> The data is taken from the subject part with the `L` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.subject.organization` | Add the `organization` information into the subject.<br /> The data is taken from the subject part with the `O` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.subject.organizationalUnit` | Add the `organizationalUnit` information into the subject.<br /> The data is taken from the subject part with the `OU` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.subject.commonName` | Add the `commonName` information into the subject.<br /> The data is taken from the subject part with the `CN` key.| false      | No      |
| `info.subject.serialNumber` | Add the `serialNumber` information into the subject.<br /> The data is taken from the subject part with the `SN` key.| false      | No      |
| `info.subject.domainComponent` | Add the `domainComponent` information into the subject.<br />The data is taken from the subject part with the `DC` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer` | The `info.issuer` selects the specific client certificate issuer details you want to add to the `X-Forwarded-Tls-Client-Cert-Info` header. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.country` | Add the `country` information into the issuer.<br /> The data is taken from the issuer part with the `C` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.province` | Add the `province` information into the issuer.<br />The data is taken from the issuer part with the `ST` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.locality` | Add the `locality` information into the issuer.<br /> The data is taken from the issuer part with the `L` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.organization` | Add the `organization` information into the issuer.<br /> The data is taken from the issuer part with the `O` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.commonName` |Add the `commonName` information into the issuer.<br /> The data is taken from the issuer part with the `CN` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.serialNumber` |Add the `serialNumber` information into the issuer.<br /> The data is taken from the issuer part with the `SN` key. <br />More information about `info` [here](#info). | false      | No      |
| `info.issuer.domainComponent` | Add the `domainComponent` information into the issuer.<br /> The data is taken from the issuer part with the `DC` key. <br />More information about `info` [here](#info). | false      | No      |

### pem

#### Data Format

The delimiters and `\n` will be removed.  
If there are more than one certificate, they are separated by a "`,`".

#### Header size

The `X-Forwarded-Tls-Client-Cert` header value could exceed the web server header size limit

The header size limit of web servers is commonly between 4kb and 8kb.  
If that turns out to be a problem, and if reconfiguring the server to allow larger headers is not an option,
one can alleviate the problem by selecting only the interesting parts of the cert,
through the use of the `info` options described below. (And by setting `pem` to false).

### info

The `info` option selects the specific client certificate details you want to add to the `X-Forwarded-Tls-Client-Cert-Info` header.

#### Data Format

The value of the header is an escaped concatenation of all the selected certificate details.
Unless specified otherwise, all the header values examples are shown unescaped, for readability.

If there are more than one certificate, they are separated by a `,`.

The following example shows such a concatenation, when all the available fields are selected:

```text
Subject="DC=org,DC=cheese,C=FR,C=US,ST=Cheese org state,ST=Cheese com state,L=TOULOUSE,L=LYON,O=Cheese,O=Cheese 2,CN=*.example.com";Issuer="DC=org,DC=cheese,C=FR,C=US,ST=Signing State,ST=Signing State 2,L=TOULOUSE,L=LYON,O=Cheese,O=Cheese 2,CN=Simple Signing CA 2";NB="1544094616";NA="1607166616";SAN="*.example.org,*.example.net,*.example.com,test@example.org,test@example.net,10.0.1.0,10.0.1.2"
```
