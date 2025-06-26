# headplane

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.6.0](https://img.shields.io/badge/AppVersion-0.6.0-informational?style=flat-square)

This helm chart deploys [Headplane](https://github.com/tale/headplane) + [Headscale](https://github.com/juanfont/headscale) and an embedded Tailscale relay in a kubernetes cluster.

## Installation

### Prerequisites
- Kubernetes cluster
- Helm installed (`helm version`)
- (Optional) OCI registry access for pulling images

### Install the Chart
```sh
# Install with default values
helm install headplane oci://harbor.lag0.com.br/library/headplane

# Install with custom values
helm install headplane oci://harbor.lag0.com.br/library/headplane -f values.yaml

```

### Upgrade the Chart
```sh
helm upgrade headplane oci://harbor.lag0.com.br/library/headplane
```

* Some config changes may require manual pod restart to take place

### Uninstall the Chart
```sh
helm uninstall headplane
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| headplane.config.headscale.config_path | string | `"/etc/headscale/config.yaml"` |  |
| headplane.config.headscale.config_strict | string | `"true"` |  |
| headplane.config.headscale.url | string | `"https://vpn.example.com"` |  |
| headplane.config.integration.kubernetes.enabled | bool | `true` |  |
| headplane.config.integration.kubernetes.pod_name | string | `"headplane-0"` |  |
| headplane.config.integration.kubernetes.validate_manifest | bool | `true` |  |
| headplane.config.server.cookie_secure | bool | `true` |  |
| headplane.config.server.host | string | `"0.0.0.0"` |  |
| headplane.config.server.port | int | `3000` |  |
| headplane.envFrom | list | `[]` |  |
| headplane.image | string | `"ghcr.io/tale/headplane:0.6.0"` |  |
| headplane.oidc.client_id | string | `"PLACEHOLDER_USE_SECRET"` |  |
| headplane.oidc.disable_api_key_login | bool | `true` |  |
| headplane.oidc.enabled | bool | `false` |  |
| headplane.oidc.issuer | string | `"https://your-oidc-issuer-url.com"` |  |
| headplane.oidc.redirect_uri | string | `"https://your-headplane-admin-domain.com/admin/oidc/callback"` |  |
| headplane.oidc.secret_name | string | `"oidc-secrets"` |  |
| headplane.oidc.token_endpoint_auth_method | string | `"client_secret_post"` |  |
| headscale.acl | string | `"{\n  \"acls\": []\n}\n"` |  |
| headscale.config.database.debug | bool | `false` |  |
| headscale.config.database.sqlite.path | string | `"/etc/headscale/db.sqlite"` |  |
| headscale.config.database.type | string | `"sqlite"` |  |
| headscale.config.derp.paths | list | `[]` |  |
| headscale.config.derp.server.automatically_add_embedded_derp_region | bool | `true` |  |
| headscale.config.derp.server.enabled | bool | `false` |  |
| headscale.config.derp.server.ipv4 | string | `"1.2.3.4"` |  |
| headscale.config.derp.server.ipv6 | string | `"2001:db8::1"` |  |
| headscale.config.derp.server.private_key_path | string | `"/var/lib/headscale/derp_server_private.key"` |  |
| headscale.config.derp.server.region_code | string | `"headscale"` |  |
| headscale.config.derp.server.region_id | int | `999` |  |
| headscale.config.derp.server.region_name | string | `"Headscale Embedded DERP"` |  |
| headscale.config.derp.server.stun_listen_addr | string | `"0.0.0.0:3478"` |  |
| headscale.config.derp.urls[0] | string | `"https://controlplane.tailscale.com/derpmap/default"` |  |
| headscale.config.dns.base_domain | string | `"headscale.vpn"` |  |
| headscale.config.dns.magic_dns | bool | `true` |  |
| headscale.config.dns.nameservers.global[0] | string | `"1.1.1.1"` |  |
| headscale.config.dns.nameservers.global[1] | string | `"8.8.8.8"` |  |
| headscale.config.grpc_allow_insecure | bool | `false` |  |
| headscale.config.grpc_listen_addr | string | `"0.0.0.0:50443"` |  |
| headscale.config.listen_addr | string | `"0.0.0.0:8080"` |  |
| headscale.config.metrics_listen_addr | string | `"0.0.0.0:9090"` |  |
| headscale.config.noise.private_key_path | string | `"/etc/headscale/noise_private.key"` |  |
| headscale.config.policy.mode | string | `"database"` |  |
| headscale.config.policy.path | string | `"/etc/headscale/acl.hujson"` |  |
| headscale.config.prefixes.allocation | string | `"sequential"` |  |
| headscale.config.prefixes.v4 | string | `"100.64.0.0/10"` |  |
| headscale.config.prefixes.v6 | string | `"fd7a:115c:a1e0::/48"` |  |
| headscale.config.server_url | string | `"https://vpn.example.com"` |  |
| headscale.envFrom | list | `[]` |  |
| headscale.image | string | `"headscale/headscale:0.26.1"` |  |
| headscale.oidc.client_id | string | `"YOUR_OIDC_CLIENT_ID_FOR_HEADSCALE"` |  |
| headscale.oidc.enabled | bool | `false` |  |
| headscale.oidc.issuer | string | `"https://your-oidc-issuer.com"` |  |
| headscale.oidc.pkce.enabled | bool | `false` |  |
| headscale.oidc.pkce.method | string | `"S256"` |  |
| headscale.oidc.secret_name | string | `"oidc-secrets"` |  |
| ingress.annotations | list | `[]` |  |
| ingress.className | string | `"nginx"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.headplaneDomain | string | `"headplane.example.com"` |  |
| ingress.headscaleDomain | string | `"vpn.example.com"` |  |
| ingress.labels | list | `[]` |  |
| ingress.tlsSecretName | string | `"headplane-tls"` |  |
| pvc.accessModes[0] | string | `"ReadWriteOnce"` |  |
| pvc.annotations | object | `{}` |  |
| pvc.enabled | bool | `true` |  |
| pvc.labels | list | `[]` |  |
| pvc.name | string | `"headscale-config"` |  |
| pvc.storage | string | `"1Gi"` |  |
| relay.config.advertise_exit_node | string | `"true"` |  |
| relay.config.authKey | string | `""` |  |
| relay.config.exit_node | string | `"example.com"` |  |
| relay.config.firewall_debug | string | `"false"` |  |
| relay.config.hostname | string | `"example.com"` |  |
| relay.config.login_server | string | `"https://vpn.example.com"` |  |
| relay.config.routes | string | `"10.0.0.0/8"` |  |
| relay.enabled | bool | `false` |  |
| relay.image | string | `"ghcr.io/tailscale/tailscale:v1.80.3"` |  |
| relay.pvc.accessModes[0] | string | `"ReadWriteOnce"` |  |
| relay.pvc.enabled | bool | `false` |  |
| relay.pvc.name | string | `"tailscale-relay-data"` |  |
| relay.pvc.storage | string | `"1Gi"` |  |

### OIDC Configuration

The chart automatically creates OIDC secrets when OIDC is enabled. Configure your OIDC provider settings in `values.yaml`:

```yaml
headplane:
  oidc:
    enabled: true
    issuer: "https://your-oidc-provider.com/application/o/headplane/"
    client_id: "headplane-client-id"
    client_secret: "your-headplane-client-secret"
    redirect_uri: "https://your-headplane-domain.com/admin/oidc/callback"
    token_endpoint_auth_method: "client_secret_post"

headscale:
  oidc:
    enabled: true
    issuer: "https://your-oidc-provider.com/application/o/headscale/"
    client_id: "headscale-client-id"
    client_secret: "your-headscale-client-secret"
```

**Important Notes:**
- The chart will automatically append `/.well-known/openid-configuration` to the Headplane issuer URL if not present
- Headscale issuer URL should be the base application URL (without `.well-known/openid-configuration`)
- Client secrets are automatically stored in Kubernetes secrets
- The API token generation job will retry if it fails initially

**OIDC Provider Setup:**
You'll need to create two applications in your OIDC provider:
1. **Headplane Application**: For admin interface access
   - Redirect URI: `https://your-headplane-domain.com/admin/oidc/callback`
2. **Headscale Application**: For VPN client authentication
   - Redirect URI: `https://your-headscale-domain.com/oidc/callback`

**Alternative Manual Secret Creation:**
If you prefer to manage secrets manually:

```sh
kubectl create secret generic oidc-secrets \
  --from-literal=HEADPLANE_OIDC__CLIENT_SECRET=your-headplane-client-secret \
  --from-literal=HEADPLANE_OIDC__CLIENT_ID=your-headplane-client-id \
  --from-literal=HEADSCALE_OIDC__CLIENT_SECRET=your-headscale-client-secret \
  --from-literal=HEADSCALE_OIDC__CLIENT_ID=your-headscale-client-id \
  -n <namespace>
```

Then omit the `client_secret` and `client_id` fields from your values.yaml.

## Tailscale Relay

Enable the embedded Tailscale relay to access cluster services via your Tailscale network:

```yaml
relay:
  enabled: true
  config:
    authKey: "tskey-auth-your-key"
    hostname: "k8s-cluster-relay"
    routes: "10.42.0.0/16,10.43.0.0/16"  # Adjust for your cluster CIDRs
```

**Setup:**
1. Generate pre-auth key: `kubectl exec headplane-0 -c headscale -- headscale preauthkey create --user <id>`
2. Create secret: `kubectl create secret generic tailscale-auth --from-literal=TS_AUTHKEY=<key>`
3. Enable route acceptance on clients: `tailscale up --accept-routes`

**Access services directly:** `curl http://service-cluster-ip:port`

## License
Copyright © 2025 antoniolago

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at:

```
http://www.apache.org/licenses/LICENSE-2.0
```

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License. 