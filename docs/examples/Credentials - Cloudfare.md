## Generate Cloudflare API Token

![](attachments/Credentials%20-%20Cloudfare-4.png)

![](attachments/Credentials%20-%20Cloudfare.png)

![](attachments/Credentials%20-%20Cloudfare-5.png)

[From external-dns docs](https://github.com/kubernetes-sigs/external-dns/blob/master/docs/tutorials/cloudflare.md)
Snippet from [Cloudflare - Getting Started](https://api.cloudflare.com/#getting-started-endpoints):

> Cloudflare's API exposes the entire Cloudflare infrastructure via a standardized programmatic interface. Using Cloudflare's API, you can do just about anything you can do on cloudflare.com via the customer dashboard.

> The Cloudflare API is a RESTful API based on HTTPS requests and JSON responses. If you are registered with Cloudflare, you can obtain your API key from the bottom of the "My Account" page, found here: [Go to My account](https://dash.cloudflare.com/profile).

API Token will be preferred for authentication if `CF_API_TOKEN` environment variable is set. Otherwise `CF_API_KEY` and `CF_API_EMAIL` should be set to run ExternalDNS with Cloudflare.

When using API Token authentication, the token should be granted Zone `Read`, DNS `Edit` privileges, and access to `All zones`.

If you would like to further restrict the API permissions to a specific zone (or zones), you also need to use the `--zone-id-filter` so that the underlying API requests only access the zones that you explicitly specify, as opposed to accessing all zones.

![](attachments/Credentials%20-%20Cloudfare-6.png)




