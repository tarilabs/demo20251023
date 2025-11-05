Deploy RH SSO
Create Keycloack resource with defaults

```yaml
kind: Keycloak
apiVersion: keycloak.org/v1alpha1
metadata:
  name: example-keycloak
  labels:
    app: sso
  namespace: trusted-artifact-signer
spec:
  instances: 1
  externalAccess:
    enabled: true
```

Access admin console (Route keycloak): https://keycloak-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com
Psw is in Secret called `credential-example-keycloak` and key `ADMIN_PASSWORD`

In keycloak Console:
- create User
  - password NOT temporary
- edit Client
  - Direct Access Grants Enabled ON
  - OAuth 2.0 Device Authorization
  - so to use user/password

## Dry run

OIDC_ISSUER_URL=https://keycloak-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com/auth/realms/master

curl -X POST --insecure -H "Content-Type: application/x-www-form-urlencoded" -d "username=user1" -d "password=user1" -d "grant_type=password" -d "scope=openid" -d "client_id=account" $OIDC_ISSUER_URL/protocol/openid-connect/token 

curl -X POST --insecure -H "Content-Type: application/x-www-form-urlencoded" -d "username=user1" -d "password=user1" -d "grant_type=password" -d "scope=openid" -d "client_id=trusted-artifact-signer" $OIDC_ISSUER_URL/protocol/openid-connect/token
echo "$TOKEN" | cut -d '.' -f2 | base64 -d 2>/dev/null | jq .

## Create TAS Secursign

```yaml
  fulcio:
...
    config:
      OIDCIssuers:
        - ClientID: trusted-artifact-signer
          Issuer: 'https://keycloak-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com/auth/realms/master'
          IssuerURL: 'https://keycloak-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com/auth/realms/master'
          Type: email
```

OIDC_ISSUER_URL=https://keycloak-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com/auth/realms/master
TUF_URL=https://tuf-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com
FULCIO_URL=https://fulcio-server-trusted-artifact-signer.apps.rosa.mmortari-rosa2.7bcr.p3.openshiftapps.com
IMAGE=quay.io/mmortari/demo20251016-lmeh-olot:latest

cosign initialize --mirror=$TUF_URL --root=$TUF_URL/root.json
TOKEN=$(curl -X POST --insecure -H "Content-Type: application/x-www-form-urlencoded" -d "username=user1" -d "password=user1" -d "grant_type=password" -d "scope=openid" -d "client_id=trusted-artifact-signer" $OIDC_ISSUER_URL/protocol/openid-connect/token  |  sed -E 's/.*"access_token":"([^"]*).*/\1/')
echo "$TOKEN" | cut -d '.' -f2 | base64 -d 2>/dev/null | jq .
COSIGN_EXPERIMENTAL=1  cosign sign -y --fulcio-url=$FULCIO_URL --identity-token=$TOKEN --oidc-issuer=$OIDC_ISSUER_URL --oidc-client-id=trusted-artifact-signer $IMAGE


# References
- https://github.com/securesign/quickstarts/blob/main/openshift/shared/cosign/keycloak-oidc-cronjob.yaml
- https://developers.redhat.com/learning/learn:sign-and-verify-artifacts-github-identity-provider-and-red-hat-trusted-artifact-signer/resource/resources:sign-and-verify-artifacts
- https://docs.redhat.com/en/documentation/red_hat_single_sign-on/7.4/html/server_installation_and_configuration_guide/operator