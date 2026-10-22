# Setup and troubleshooting notes

Use this file to document the final configuration you actually used. Do not paste credentials or private keys.

## Record your configuration

- AWS Region: `us-east-1`
- ALB listener: HTTP `:80`
- Target group protocol/port: HTTP `:8000`
- Health check path: `/`
- Target count: `2`
- Target status at validation: both `Healthy`

## Validation commands

From Windows PowerShell:

```powershell
Test-NetConnection <your-alb-dns-name> -Port 80
curl.exe -v --max-time 10 http://<your-alb-dns-name>/
```

From a host that can reach a private target:

```bash
curl -i --max-time 5 http://<private-instance-ip>:8000/
```

## Important operational note

The Python built-in HTTP server was started interactively for testing. It is not a production service and will stop when its process is terminated. Document any later automation separately.
