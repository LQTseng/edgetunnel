## EdgeTunnel

This project comes from [zizifn/edgetunnel](https://github.com/zizifn/edgetunnel)

## Features

- Support using non-standard ports as proxy ports.
- Support using KV to configure uuid, proxy ip, proxy port, and socks5 address  
~~( Although deployment is automatic, I don't like to see many deployment records that cannot be deleted. Now I only need to modify the value of KV without deploying. )~~

## How to configure KV

1. Log in to the [Cloudflare dashboard](https://dash.cloudflare.com/).
2. Select Workers & Pages > KV.
3. Select Create a namespace.
4. Enter a name for your namespace.
5. Select Add.
6. View the created namespace
7. Add entries as shown in the table below

|  Key   |            Value（example）            |
| ------ | -------------------------------------- |
| uuid   | `d342d11e-d424-4583-b36e-524ab1f0afa4` |
| ip     | `1.1.1.1 `                             |
| port   | `443`                                  |
| socks5 | `user:pass@host:port`  or  `host:port` |

> - The uuid needs to be legal
> - Port can be omitted, default to 443
> - Socks5 can be omitted. Setting the address will ignore proxyIP. The user name and password do not contain special characters


8. Go to Workers & Pages.
9. Select your Worker.
10. Select Settings > Variables.
11. Go to KV Namespace Bindings.
12. Select Add binding.
13. Set the variable name to "PROXY", then select the namespace created above and click "Save and Deploy"

| Variable name |             KV Namespace             |
| ------------- | ------------------------------------ |
| PROXY         | *Select the namespace created above* |

### How to generate your own UUID

[ *Windows* ] Press "Win + R", input cmd and run:  

```
Powershell -NoExit -Command "[guid]::NewGuid()"
```