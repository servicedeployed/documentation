# App - Credentials - Cloudflare

## Installation

### Certmanager Credentials

In order for the ClusterIssuer to communicate with Cloudflare, you have to add in a secret for your Cloudflare api token.

#### Add Secret
Secret Name: `cloudflare-credentials`
Namespace: `cert-manager`
Secret Key: `api-token`
Secret Value: Cloudflare API Token - 1Password Vault

![](attachments/CRD%20-%20Cloudflare%20ClusterIssuer.png)

![](attachments/CRD%20-%20Cloudflare%20ClusterIssuer-1.png)

![](attachments/CRD%20-%20Cloudflare%20ClusterIssuer-2.png)

![](attachments/CRD%20-%20Cloudflare%20ClusterIssuer-3.png)

### Add CRD - ClusterIssuer

Cloudflare - ClusterIssuer CRD

```yaml
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: cloudflare-issuer
spec:
  acme:
    email: contact@megaportone.com
    preferredChain: ""
    privateKeySecretRef:
      name: letsencrypt-account-key
    server: https://acme-v02.api.letsencrypt.org/directory
    solvers:
    - dns01:
        cloudflare:
          email: contact@megaportone.com
          apiTokenSecretRef:
            name: cloudflare-credentials
            key: api-token
```