# 2025-11-12

Using the Pod with the ODH Connection results in:

<details>

```json
{
    "Base64Signature": "MEUCIQC8UlYCMxcz33ifOb819FKUmTDFft9faDGaGkI8hkGGSAIgUgq6tylHzz5Lsafxd29kktHlgzo/NaxpRpSEwNKtcDw=",
    "Payload": "eyJjcml0aWNhbCI6eyJpZGVudGl0eSI6eyJkb2NrZXItcmVmZXJlbmNlIjoicXVheS5pby9tbW9ydGFyaS9kZW1vMjAyNTEwMTYtbG1laC1vbG90In0sImltYWdlIjp7ImRvY2tlci1tYW5pZmVzdC1kaWdlc3QiOiJzaGEyNTY6MjBmM2I4ZGE0ZjRhZDFmYjZkNzIxMGQzMThlMmFiNmI0ZjIwYjgzZWQyOWU4OWJmNmRiYzdkOTM3ZjY0MjAwMiJ9LCJ0eXBlIjoiY29zaWduIGNvbnRhaW5lciBpbWFnZSBzaWduYXR1cmUifSwib3B0aW9uYWwiOm51bGx9",
    "Cert": {
        "Raw": "MIIDTzCCAtWgAwIBAgIUbtpQsdSYa2M2jAWLWDK7uTkKbPUwCgYIKoZIzj0EAwMwLDEQMA4GA1UEChMHUmVkIEhhdDEYMBYGA1UEAxMPZnVsY2lvLmhvc3RuYW1lMB4XDTI1MTExMjEwMzUyMVoXDTI1MTExMjEwNDUyMVowADBZMBMGByqGSM49AgEGCCqGSM49AwEHA0IABEulIJB9zw8aNc2aQcxxOX/qgm5K4ZonYUJP2DO1IcUcIC/x4mwcPkCRcm+Ow9su8OKr7qxaxm1DYmudmK3LnDqjggH/MIIB+zAOBgNVHQ8BAf8EBAMCB4AwEwYDVR0lBAwwCgYIKwYBBQUHAwMwHQYDVR0OBBYEFII4ZNIj9r6s217o+D/8mf+wtocIMB8GA1UdIwQYMBaAFKQQygFYjAnWgR1ZQCYmcKP4T8ZVME4GA1UdEQEB/wREMEKGQGh0dHBzOi8va3ViZXJuZXRlcy5pby9uYW1lc3BhY2VzL2RzLXByajEvc2VydmljZWFjY291bnRzL2RlZmF1bHQwWQYKKwYBBAGDvzABAQRLaHR0cHM6Ly9yaC1vaWRjLnMzLnVzLWVhc3QtMS5hbWF6b25hd3MuY29tLzIzYzczNHN0M3BuN2wxNjdtcTk3ZDBvdDg4NDhsZ3JsMFsGCisGAQQBg78wAQgETQxLaHR0cHM6Ly9yaC1vaWRjLnMzLnVzLWVhc3QtMS5hbWF6b25hd3MuY29tLzIzYzczNHN0M3BuN2wxNjdtcTk3ZDBvdDg4NDhsZ3JsMIGLBgorBgEEAdZ5AgQCBH0EewB5AHcAnOiGvOvopnddHqI8eQSs0IqOOf955zem9hfXi8ejBz4AAAGad6Je2QAABAMASDBGAiEA+xv1ElzToZ7AxzbU7LQg8ldSblp60F8KDgf7caf+VUMCIQDp3m0Lb5n70NKTTU6ASaozNVTFWLW+Q7EvZx7OspwpZzAKBggqhkjOPQQDAwNoADBlAjEAkPlJTLYphAMPduWk7xeHHYoFzM0fL3Ri/Y1rnSpPN3D5s0CKjFZFGJYEDt+E4pdxAjBBvRmUiROFNI3g3CuOCAdfiQjUaweWXfdg5JLxLAQwm6U4HjM18fXROG96M6lJhcg=",
        "RawTBSCertificate": "MIIC1aADAgECAhRu2lCx1JhrYzaMBYtYMru5OQps9TAKBggqhkjOPQQDAzAsMRAwDgYDVQQKEwdSZWQgSGF0MRgwFgYDVQQDEw9mdWxjaW8uaG9zdG5hbWUwHhcNMjUxMTEyMTAzNTIxWhcNMjUxMTEyMTA0NTIxWjAAMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAES6UgkH3PDxo1zZpBzHE5f+qCbkrhmidhQk/YM7UhxRwgL/HibBw+QJFyb47D2y7w4qvurFrGbUNia52YrcucOqOCAf8wggH7MA4GA1UdDwEB/wQEAwIHgDATBgNVHSUEDDAKBggrBgEFBQcDAzAdBgNVHQ4EFgQUgjhk0iP2vqzbXuj4P/yZ/7C2hwgwHwYDVR0jBBgwFoAUpBDKAViMCdaBHVlAJiZwo/hPxlUwTgYDVR0RAQH/BEQwQoZAaHR0cHM6Ly9rdWJlcm5ldGVzLmlvL25hbWVzcGFjZXMvZHMtcHJqMS9zZXJ2aWNlYWNjb3VudHMvZGVmYXVsdDBZBgorBgEEAYO/MAEBBEtodHRwczovL3JoLW9pZGMuczMudXMtZWFzdC0xLmFtYXpvbmF3cy5jb20vMjNjNzM0c3QzcG43bDE2N21xOTdkMG90ODg0OGxncmwwWwYKKwYBBAGDvzABCARNDEtodHRwczovL3JoLW9pZGMuczMudXMtZWFzdC0xLmFtYXpvbmF3cy5jb20vMjNjNzM0c3QzcG43bDE2N21xOTdkMG90ODg0OGxncmwwgYsGCisGAQQB1nkCBAIEfQR7AHkAdwCc6Ia86+imd10eojx5BKzQio45/3nnN6b2F9eLx6MHPgAAAZp3ol7ZAAAEAwBIMEYCIQD7G/USXNOhnsDHNtTstCDyV1JuWnrQXwoOB/txp/5VQwIhAOnebQtvmfvQ0pNNToBJqjM1VMVYtb5DsS9nHs6ynCln",
        "RawSubjectPublicKeyInfo": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAES6UgkH3PDxo1zZpBzHE5f+qCbkrhmidhQk/YM7UhxRwgL/HibBw+QJFyb47D2y7w4qvurFrGbUNia52YrcucOg==",
        "RawSubject": "MAA=",
        "RawIssuer": "MCwxEDAOBgNVBAoTB1JlZCBIYXQxGDAWBgNVBAMTD2Z1bGNpby5ob3N0bmFtZQ==",
        "Signature": "MGUCMQCQ+UlMtimEAw925aTvF4cdigXMzR8vdGL9jWudKk83cPmzQIqMVkUYlgQO34Til3ECMEG9GZSJE4U0jeDcK44IB1+JCNRrB5Zd92DkkvEsBDCbpTgeMzXx9dE4b3ozqUmFyA==",
        "SignatureAlgorithm": 11,
        "PublicKeyAlgorithm": 3,
        "PublicKey": {
            "Curve": {},
            "X": 34215218160798045498119463233130422182752882216439399599471780687087392638236,
            "Y": 14558722391911977860919183631563440000803821639720389538197964404915039870010
        },
        "Version": 3,
        "SerialNumber": 632857576739343251643536980893913308008693787893,
        "Issuer": {
            "Country": null,
            "Organization": [
                "Red Hat"
            ],
            "OrganizationalUnit": null,
            "Locality": null,
            "Province": null,
            "StreetAddress": null,
            "PostalCode": null,
            "SerialNumber": "",
            "CommonName": "fulcio.hostname",
            "Names": [
                {
                    "Type": [
                        2,
                        5,
                        4,
                        10
                    ],
                    "Value": "Red Hat"
                },
                {
                    "Type": [
                        2,
                        5,
                        4,
                        3
                    ],
                    "Value": "fulcio.hostname"
                }
            ],
            "ExtraNames": null
        },
        "Subject": {
            "Country": null,
            "Organization": null,
            "OrganizationalUnit": null,
            "Locality": null,
            "Province": null,
            "StreetAddress": null,
            "PostalCode": null,
            "SerialNumber": "",
            "CommonName": "",
            "Names": null,
            "ExtraNames": null
        },
        "NotBefore": "2025-11-12T10:35:21Z",
        "NotAfter": "2025-11-12T10:45:21Z",
        "KeyUsage": 1,
        "Extensions": [
            {
                "Id": [
                    2,
                    5,
                    29,
                    15
                ],
                "Critical": true,
                "Value": "AwIHgA=="
            },
            {
                "Id": [
                    2,
                    5,
                    29,
                    37
                ],
                "Critical": false,
                "Value": "MAoGCCsGAQUFBwMD"
            },
            {
                "Id": [
                    2,
                    5,
                    29,
                    14
                ],
                "Critical": false,
                "Value": "BBSCOGTSI/a+rNte6Pg//Jn/sLaHCA=="
            },
            {
                "Id": [
                    2,
                    5,
                    29,
                    35
                ],
                "Critical": false,
                "Value": "MBaAFKQQygFYjAnWgR1ZQCYmcKP4T8ZV"
            },
            {
                "Id": [
                    2,
                    5,
                    29,
                    17
                ],
                "Critical": true,
                "Value": "MEKGQGh0dHBzOi8va3ViZXJuZXRlcy5pby9uYW1lc3BhY2VzL2RzLXByajEvc2VydmljZWFjY291bnRzL2RlZmF1bHQ="
            },
            {
                "Id": [
                    1,
                    3,
                    6,
                    1,
                    4,
                    1,
                    57264,
                    1,
                    1
                ],
                "Critical": false,
                "Value": "aHR0cHM6Ly9yaC1vaWRjLnMzLnVzLWVhc3QtMS5hbWF6b25hd3MuY29tLzIzYzczNHN0M3BuN2wxNjdtcTk3ZDBvdDg4NDhsZ3Js"
            },
            {
                "Id": [
                    1,
                    3,
                    6,
                    1,
                    4,
                    1,
                    57264,
                    1,
                    8
                ],
                "Critical": false,
                "Value": "DEtodHRwczovL3JoLW9pZGMuczMudXMtZWFzdC0xLmFtYXpvbmF3cy5jb20vMjNjNzM0c3QzcG43bDE2N21xOTdkMG90ODg0OGxncmw="
            },
            {
                "Id": [
                    1,
                    3,
                    6,
                    1,
                    4,
                    1,
                    11129,
                    2,
                    4,
                    2
                ],
                "Critical": false,
                "Value": "BHsAeQB3AJzohrzr6KZ3XR6iPHkErNCKjjn/eec3pvYX14vHowc+AAABmneiXtkAAAQDAEgwRgIhAPsb9RJc06GewMc21Oy0IPJXUm5aetBfCg4H+3Gn/lVDAiEA6d5tC2+Z+9DSk01OgEmqMzVUxVi1vkOxL2cezrKcKWc="
            }
        ],
        "ExtraExtensions": null,
        "UnhandledCriticalExtensions": null,
        "ExtKeyUsage": [
            3
        ],
        "UnknownExtKeyUsage": null,
        "BasicConstraintsValid": false,
        "IsCA": false,
        "MaxPathLen": 0,
        "MaxPathLenZero": false,
        "SubjectKeyId": "gjhk0iP2vqzbXuj4P/yZ/7C2hwg=",
        "AuthorityKeyId": "pBDKAViMCdaBHVlAJiZwo/hPxlU=",
        "OCSPServer": null,
        "IssuingCertificateURL": null,
        "DNSNames": null,
        "EmailAddresses": null,
        "IPAddresses": null,
        "URIs": [
            {
                "Scheme": "https",
                "Opaque": "",
                "User": null,
                "Host": "kubernetes.io",
                "Path": "/namespaces/ds-prj1/serviceaccounts/default",
                "RawPath": "",
                "OmitHost": false,
                "ForceQuery": false,
                "RawQuery": "",
                "Fragment": "",
                "RawFragment": ""
            }
        ],
        "PermittedDNSDomainsCritical": false,
        "PermittedDNSDomains": null,
        "ExcludedDNSDomains": null,
        "PermittedIPRanges": null,
        "ExcludedIPRanges": null,
        "PermittedEmailAddresses": null,
        "ExcludedEmailAddresses": null,
        "PermittedURIDomains": null,
        "ExcludedURIDomains": null,
        "CRLDistributionPoints": null,
        "PolicyIdentifiers": null,
        "Policies": null,
        "InhibitAnyPolicy": 0,
        "InhibitAnyPolicyZero": false,
        "InhibitPolicyMapping": 0,
        "InhibitPolicyMappingZero": false,
        "RequireExplicitPolicy": 0,
        "RequireExplicitPolicyZero": false,
        "PolicyMappings": null
    },
    "Chain": [
        {
            "Raw": "MIIB9TCCAXugAwIBAgIUbHMoGmz1Sch29ikdi6mCq8IaINowCgYIKoZIzj0EAwMwLDEQMA4GA1UEChMHUmVkIEhhdDEYMBYGA1UEAxMPZnVsY2lvLmhvc3RuYW1lMB4XDTI1MTAyMjA5NDIyM1oXDTM1MTAyMDA5NDIyM1owLDEQMA4GA1UEChMHUmVkIEhhdDEYMBYGA1UEAxMPZnVsY2lvLmhvc3RuYW1lMHYwEAYHKoZIzj0CAQYFK4EEACIDYgAEoyqscwn3RczsC+DRDu1gmYG2xAX9c5Rjcht1+lNAjHcEHfT12Qb31YIdCd0jA/bpmhGm5xZxucgPLAVuSoY93GqOW1t7trEZKEkX7Gs+HvyzYWAVl00+9a/eVWK8w0Rno14wXDAOBgNVHQ8BAf8EBAMCAQYwDwYDVR0TAQH/BAUwAwEB/zAdBgNVHQ4EFgQUpBDKAViMCdaBHVlAJiZwo/hPxlUwGgYDVR0RBBMwEYEPamRvZUByZWRoYXQuY29tMAoGCCqGSM49BAMDA2gAMGUCMQDRPudD0x6uNWYKZj1reYV4tLKbWkHEZJMygeF291uoQ48PTIFbxft3KsyRbLTdzJ8CMFFp68T2giA0NEyz1j+Kbd/BcSFr5f7nz8u0aQKsGqmhmKDcTwkllBix6AE7xpskIQ==",
            "RawTBSCertificate": "MIIBe6ADAgECAhRscygabPVJyHb2KR2LqYKrwhog2jAKBggqhkjOPQQDAzAsMRAwDgYDVQQKEwdSZWQgSGF0MRgwFgYDVQQDEw9mdWxjaW8uaG9zdG5hbWUwHhcNMjUxMDIyMDk0MjIzWhcNMzUxMDIwMDk0MjIzWjAsMRAwDgYDVQQKEwdSZWQgSGF0MRgwFgYDVQQDEw9mdWxjaW8uaG9zdG5hbWUwdjAQBgcqhkjOPQIBBgUrgQQAIgNiAASjKqxzCfdFzOwL4NEO7WCZgbbEBf1zlGNyG3X6U0CMdwQd9PXZBvfVgh0J3SMD9umaEabnFnG5yA8sBW5Khj3cao5bW3u2sRkoSRfsaz4e/LNhYBWXTT71r95VYrzDRGejXjBcMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBSkEMoBWIwJ1oEdWUAmJnCj+E/GVTAaBgNVHREEEzARgQ9qZG9lQHJlZGhhdC5jb20=",
            "RawSubjectPublicKeyInfo": "MHYwEAYHKoZIzj0CAQYFK4EEACIDYgAEoyqscwn3RczsC+DRDu1gmYG2xAX9c5Rjcht1+lNAjHcEHfT12Qb31YIdCd0jA/bpmhGm5xZxucgPLAVuSoY93GqOW1t7trEZKEkX7Gs+HvyzYWAVl00+9a/eVWK8w0Rn",
            "RawSubject": "MCwxEDAOBgNVBAoTB1JlZCBIYXQxGDAWBgNVBAMTD2Z1bGNpby5ob3N0bmFtZQ==",
            "RawIssuer": "MCwxEDAOBgNVBAoTB1JlZCBIYXQxGDAWBgNVBAMTD2Z1bGNpby5ob3N0bmFtZQ==",
            "Signature": "MGUCMQDRPudD0x6uNWYKZj1reYV4tLKbWkHEZJMygeF291uoQ48PTIFbxft3KsyRbLTdzJ8CMFFp68T2giA0NEyz1j+Kbd/BcSFr5f7nz8u0aQKsGqmhmKDcTwkllBix6AE7xpskIQ==",
            "SignatureAlgorithm": 11,
            "PublicKeyAlgorithm": 3,
            "PublicKey": {
                "Curve": {},
                "X": 25113652667401269490674486773967007255573634067745100244669376297808296566407265924768568777578829261469427167393513,
                "Y": 23713382187904557188644527939951649599988448820231045557284346771280133764686868284291649584422088783728959222400103
            },
            "Version": 3,
            "SerialNumber": 619139082430414733406184398947254967188139417818,
            "Issuer": {
                "Country": null,
                "Organization": [
                    "Red Hat"
                ],
                "OrganizationalUnit": null,
                "Locality": null,
                "Province": null,
                "StreetAddress": null,
                "PostalCode": null,
                "SerialNumber": "",
                "CommonName": "fulcio.hostname",
                "Names": [
                    {
                        "Type": [
                            2,
                            5,
                            4,
                            10
                        ],
                        "Value": "Red Hat"
                    },
                    {
                        "Type": [
                            2,
                            5,
                            4,
                            3
                        ],
                        "Value": "fulcio.hostname"
                    }
                ],
                "ExtraNames": null
            },
            "Subject": {
                "Country": null,
                "Organization": [
                    "Red Hat"
                ],
                "OrganizationalUnit": null,
                "Locality": null,
                "Province": null,
                "StreetAddress": null,
                "PostalCode": null,
                "SerialNumber": "",
                "CommonName": "fulcio.hostname",
                "Names": [
                    {
                        "Type": [
                            2,
                            5,
                            4,
                            10
                        ],
                        "Value": "Red Hat"
                    },
                    {
                        "Type": [
                            2,
                            5,
                            4,
                            3
                        ],
                        "Value": "fulcio.hostname"
                    }
                ],
                "ExtraNames": null
            },
            "NotBefore": "2025-10-22T09:42:23Z",
            "NotAfter": "2035-10-20T09:42:23Z",
            "KeyUsage": 96,
            "Extensions": [
                {
                    "Id": [
                        2,
                        5,
                        29,
                        15
                    ],
                    "Critical": true,
                    "Value": "AwIBBg=="
                },
                {
                    "Id": [
                        2,
                        5,
                        29,
                        19
                    ],
                    "Critical": true,
                    "Value": "MAMBAf8="
                },
                {
                    "Id": [
                        2,
                        5,
                        29,
                        14
                    ],
                    "Critical": false,
                    "Value": "BBSkEMoBWIwJ1oEdWUAmJnCj+E/GVQ=="
                },
                {
                    "Id": [
                        2,
                        5,
                        29,
                        17
                    ],
                    "Critical": false,
                    "Value": "MBGBD2pkb2VAcmVkaGF0LmNvbQ=="
                }
            ],
            "ExtraExtensions": null,
            "UnhandledCriticalExtensions": null,
            "ExtKeyUsage": null,
            "UnknownExtKeyUsage": null,
            "BasicConstraintsValid": true,
            "IsCA": true,
            "MaxPathLen": -1,
            "MaxPathLenZero": false,
            "SubjectKeyId": "pBDKAViMCdaBHVlAJiZwo/hPxlU=",
            "AuthorityKeyId": null,
            "OCSPServer": null,
            "IssuingCertificateURL": null,
            "DNSNames": null,
            "EmailAddresses": [
                "jdoe@redhat.com"
            ],
            "IPAddresses": null,
            "URIs": null,
            "PermittedDNSDomainsCritical": false,
            "PermittedDNSDomains": null,
            "ExcludedDNSDomains": null,
            "PermittedIPRanges": null,
            "ExcludedIPRanges": null,
            "PermittedEmailAddresses": null,
            "ExcludedEmailAddresses": null,
            "PermittedURIDomains": null,
            "ExcludedURIDomains": null,
            "CRLDistributionPoints": null,
            "PolicyIdentifiers": null,
            "Policies": null,
            "InhibitAnyPolicy": 0,
            "InhibitAnyPolicyZero": false,
            "InhibitPolicyMapping": 0,
            "InhibitPolicyMappingZero": false,
            "RequireExplicitPolicy": 0,
            "RequireExplicitPolicyZero": false,
            "PolicyMappings": null
        }
    ],
    "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCIyDgKEr4ceqpCxHaKWaXmPGYvN/yIYP5ds5Y7AVNSRgIhAJNLxPemwlCFttzJiqRgNw7pvDl3JEICmSTX6QvFEngM",
        "Payload": {
            "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIxOTQxOGU1YWFlOWQ3ODdhNWJiOTNmMjJkYTM1NDc4M2FjMzIwZDY4MzhiOTM2M2NlMDAxODIzYTkzNDgwNzUzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUM4VWxZQ014Y3ozM2lmT2I4MTlGS1VtVERGZnQ5ZmFER2FHa0k4aGtHR1NBSWdVZ3E2dHlsSHp6NUxzYWZ4ZDI5a2t0SGxnem8vTmF4cFJwU0V3Tkt0Y0R3PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUlVla05EUVhSWFowRjNTVUpCWjBsVlluUndVWE5rVTFsaE1rMHlha0ZYVEZkRVN6ZDFWR3RMWWxCVmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RFUkZVVTFCTkVkQk1WVkZRMmhOU0ZWdFZtdEpSV2hvWkVSRldVMUNXVWRCTVZWRlFYaE5VRnB1Vm5OWk1teDJURzFvZG1NelVuVlpWekZzVFVJMFdBcEVWRWt4VFZSRmVFMXFSWGROZWxWNVRWWnZXRVJVU1RGTlZFVjRUV3BGZDA1RVZYbE5WbTkzUVVSQ1drMUNUVWRDZVhGSFUwMDBPVUZuUlVkRFEzRkhDbE5OTkRsQmQwVklRVEJKUVVKRmRXeEpTa0k1ZW5jNFlVNWpNbUZSWTNoNFQxZ3ZjV2R0TlVzMFdtOXVXVlZLVURKRVR6RkpZMVZqU1VNdmVEUnRkMk1LVUd0RFVtTnRLMDkzT1hOMU9FOUxjamR4ZUdGNGJURkVXVzExWkcxTE0weHVSSEZxWjJkSUwwMUpTVUlyZWtGUFFtZE9Wa2hST0VKQlpqaEZRa0ZOUXdwQ05FRjNSWGRaUkZaU01HeENRWGQzUTJkWlNVdDNXVUpDVVZWSVFYZE5kMGhSV1VSV1VqQlBRa0paUlVaSlNUUmFUa2xxT1hJMmN6SXhOMjhyUkM4NENtMW1LM2QwYjJOSlRVSTRSMEV4VldSSmQxRlpUVUpoUVVaTFVWRjVaMFpaYWtGdVYyZFNNVnBSUTFsdFkwdFFORlE0V2xaTlJUUkhRVEZWWkVWUlJVSUtMM2RTUlUxRlMwZFJSMmd3WkVoQ2VrOXBPSFpoTTFacFdsaEtkVnBZVW14amVUVndZbms1ZFZsWE1XeGpNMEpvV1RKV2Vrd3lVbnBNV0VKNVlXcEZkZ3BqTWxaNVpHMXNhbHBYUm1wWk1qa3hZbTVTZWt3eVVteGFiVVl4WWtoUmQxZFJXVXRMZDFsQ1FrRkhSSFo2UVVKQlVWSk1ZVWhTTUdOSVRUWk1lVGw1Q21GRE1YWmhWMUpxVEc1TmVreHVWbnBNVjFab1l6TlJkRTFUTldoaVYwWTJZakkxYUdRelRYVlpNamwwVEhwSmVsbDZZM3BPU0U0d1RUTkNkVTR5ZDNnS1RtcGtkR05VYXpOYVJFSjJaRVJuTkU1RWFITmFNMHB6VFVaelIwTnBjMGRCVVZGQ1p6YzRkMEZSWjBWVVVYaE1ZVWhTTUdOSVRUWk1lVGw1WVVNeGRncGhWMUpxVEc1TmVreHVWbnBNVjFab1l6TlJkRTFUTldoaVYwWTJZakkxYUdRelRYVlpNamwwVEhwSmVsbDZZM3BPU0U0d1RUTkNkVTR5ZDNoT2FtUjBDbU5VYXpOYVJFSjJaRVJuTkU1RWFITmFNMHB6VFVsSFRFSm5iM0pDWjBWRlFXUmFOVUZuVVVOQ1NEQkZaWGRDTlVGSVkwRnVUMmxIZGs5MmIzQnVaR1FLU0hGSk9HVlJVM013U1hGUFQyWTVOVFY2WlcwNWFHWllhVGhsYWtKNk5FRkJRVWRoWkRaS1pUSlJRVUZDUVUxQlUwUkNSMEZwUlVFcmVIWXhSV3g2VkFwdldqZEJlSHBpVlRkTVVXYzRiR1JUWW14d05qQkdPRXRFWjJZM1kyRm1LMVpWVFVOSlVVUndNMjB3VEdJMWJqY3dUa3RVVkZVMlFWTmhiM3BPVmxSR0NsZE1WeXRSTjBWMlduZzNUM053ZDNCYWVrRkxRbWRuY1docmFrOVFVVkZFUVhkT2IwRkVRbXhCYWtWQmExQnNTbFJNV1hCb1FVMVFaSFZYYXpkNFpVZ0tTRmx2Um5wTk1HWk1NMUpwTDFreGNtNVRjRkJPTTBRMWN6QkRTMnBHV2taSFNsbEZSSFFyUlRSd1pIaEJha0pDZGxKdFZXbFNUMFpPU1RObk0wTjFUd3BEUVdSbWFWRnFWV0YzWlZkWVptUm5OVXBNZUV4QlVYZHRObFUwU0dwTk1UaG1XRkpQUnprMlRUWnNTbWhqWnowS0xTMHRMUzFGVGtRZ1EwVlNWRWxHU1VOQlZFVXRMUzB0TFFvPSJ9fX19",
            "integratedTime": 1762943721,
            "logIndex": 696097128,
            "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
    },
    "RFC3161Timestamp": null
}
```

</details>

this is using the ROSA OIDC config as we discussed from

```
<apiserver>/.well-known/openid-configuration
```

yes

```sh
APISERVER=$(oc whoami --show-server)
TOKEN=$(oc whoami -t)
curl -sS -H "Authorization: Bearer $TOKEN" "$APISERVER/.well-known/openid-configuration" | jq
```

results in:

```
{
  "issuer": "https://rh-oidc.s3.us-east-1.amazonaws.com/23c734st3pn7l167mq97d0ot8848lgrl",
  "jwks_uri": "https://rh-oidc.s3.us-east-1.amazonaws.com/23c734st3pn7l167mq97d0ot8848lgrl/openid/v1/jwks",
  "response_types_supported": [
    "id_token"
  ],
  "subject_types_supported": [
    "public"
  ],
  "id_token_signing_alg_values_supported": [
    "RS256"
  ]
}
```

the signature:

```sh
IMAGE=quay.io/mmortari/demo20251016-lmeh-olot@sha256:20f3b8da4f4ad1fb6d7210d318e2ab6b4f20b83ed29e89bf6dbc7d937f642002              
cosign download signature "$IMAGE" | jq -r '.Cert.Extensions[] | select(.Id == [1,3,6,1,4,1,57264,1,1]) | .Value' | base64 --decode
```

results in:

```
https://rh-oidc.s3.us-east-1.amazonaws.com/23c734st3pn7l167mq97d0ot8848lgrl
```

Although the best-practice is to use `audience: str[]`, like in:

```yaml
  volumes:
  - name: sa-token
    projected:
      sources:
      - serviceAccountToken:
          path: token
          audience: "sigstore"
```

it could be just easier to configure the TAS `Securesign` CR with this as the intended `aud` in:

```yaml
  fulcio:
    config:
      MetaIssuers:
      - ClientID: sigstore # <-- here place the OIDC URL as considered stable
        Issuer: 'https://*.*.*.amazonaws.com/*'
        Type: kubernetes
```
