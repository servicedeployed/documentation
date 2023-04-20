# App - External DNS

## Retrieve Cloudflare Credentials

See [Retrieving Cloudflare Credentials](../../secrets/cloudflare-credentials/index.md)

## Installation

### Chart Location

![](attachments/App%20-%20External%20DNS-1.png)

### Overview

![](attachments/App%20-%20External%20DNS-1.png)

### Installation

#### Add Secret

Secret Name: `cloudflare-credentials`
Namespace: `external-dns`
Secret Key: `api-token`
Secret Value: Cloudflare API Token - 1Password Vault

![](attachments/CRD%20-%20Cloudflare%20ClusterIssuer.png)

![](attachments/App%20-%20External%20DNS-3.png)

![](attachments/CRD%20-%20Cloudflare%20ClusterIssuer-2.png)

![](attachments/App%20-%20External%20DNS-5.png)

### Verify

Double check that the secret name, namespace, and keys match up with the referenced values below.

### Values

```yaml
provider: cloudflare
domainFilters:
  - servicedeployed.net
env:
  - name: CF_API_TOKEN
    valueFrom:
      secretKeyRef:
        name: cloudflare-credentials
        key: api-token
```

### Deployment

![](attachments/App%20-%20External%20DNS-6.png)

![](attachments/App%20-%20External%20DNS-7.png)

### Running Application

![](attachments/App%20-%20External%20DNS-8.png)


