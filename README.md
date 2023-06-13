# DCSA-CA-Emulator
DCSA CA Emulator is a spring boot web service developed using Spring Boot and Java that emulates the behavior of a CA (certificate authority ). It allows developers to test their need for EBL transferable documents. The emulator tool provides a REST interface that allows users to request their certificate for singing. The CA Emulator tool is designed can be integrated with other Spring Boot and Java applications.



It has an ocsp (Online Certificate Status Protocol) server singing revokes and checks the status of the current certificate.

There are several REST endpoints defined:-

GET: http://localhost:9001/ebl/getCertificate returns a file when requested by the browser.

GET: http://localhost:9001/ebl/isClientCertificateSigned

POST: http://localhost:9001/ebl/signed/makeClientCertificate by the following body:-

```json
{
"commonName": "example.com",
"organizationalUnit": "IT",
"organization": "Example Inc.",
"locality": "Netherlands",
"state": "Amsterdam",
"country": "Netherlands",
"startDate": "2023-01-01T00:00:00.000Z",
"endDate": "2023-12-01T00:00:00.000Z",
"publicKey": "-----BEGIN PUBLIC KEY-----MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsh0vuDi15PkeIDB8WqnLekzO6F1y4ZvHMTNYAubvTUOvylEoZndDg5/KiXA6CuWpyhmKeYTBEtzjsTzh+CeB8P5IawntgPH1EnfUYpP7yhCc5W5cDNud4Z5lCB42xGNBIwWbJR8QTtEABTIrnqBaA5/jkdlwyMI/8w8lusTmCEhf/BIlM2Xcbfety+Xmuh1Bv/OTCt70BvO+LsOCkq7cyUg0m3xN9+u6uyL+P848cri57o2dpk75ChWrtnwBrwy8Xq20cua9tXwR/KE2Jq0xAbCqVLMtFNlla9JK5rMuQBQp5LFEh3y4wIjTscwX5tgY84MoWpyoVuVtW0vkFSpFnwIDAQAB-----END PUBLIC KEY-----"
}
```


GET: http://localhost:9001/ebl/actuator/mappings

GET: http://localhost:9001/ebl/isValid

GET: http://localhost:9001/ebl/allDistributionList

GET: http://localhost:9001/ebl/getCertificate?fileName=test.cert

POST: http://localhost:9001/ebl/addDistributionList body:


{
"crlUri": "http://www.certificadodigital.com.br/repositorio/lcr/serasarfbv2.crl"
}


PUT: http://localhost:9001/ebl/revokeSignature body attach a certificate file as form-data

DELETE: http://localhost:9001/ebl/removeDistributionList with body:

```json
{
"crlUri": "http://www.certificadodigital.com.br/repositorio/lcr/serasarfbv2.crl"
}
 ```
