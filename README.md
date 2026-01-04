# ARCTIC-Docker

ARCTIC's official installation guide using Docker.

## Installation

Notes
```
- Port 80 must be available on the host
- TLS certificates (if required) go in ./certs
- Provider JAR files go in ./providers
- First startup make take a bit longer while database sets up
```

To install using the docker image, follow the commands below:

```bash
git clone https://github.com/CyberBelligerent/ARCTIC-Docker.git
cd ARCTIC-Docker
```

Create your environment file
```bash
cp .env.example .env
```
Edit .env and set:
- ARCTIC admin username/password
- Database settings (If you do not want default)

Start ARCTIC:
```bash
docker compose up -d
```

Access the UI at:
```
http://localhost
```

## Provider Usage (DNS & HTTPS)

**If your provider endpoint is accessed via HTTP using an IP address, this step can be skipped**

If your provider endpoint uses HTTPS, it will almost always rely on a DNS name. In this case, ARCTIC must be able to resolve the DNS name from inside the Docker container.

To ensure ARCTIC can resolve the provider hostname, add an `extra_hosts` entry to your `docker-compose.yml`:
```yaml
  arctic-app:
    extra_hosts:
      - "{DNS_NAME}:{IP}"
```

**Example**
```yaml
  arctic-app:
    extra_hosts:
      - "openstack.example.lab:192.168.1.210"
```

When setting the provider enpoint inside of ARCTIC, **use the DNS name** (`openstack.example.local:5000/v3`) as the endpoint, NOT the IP address.

This makes sure the following:
- TLS certificate hostname validation succeeds
- ARCTIC connects to the correct provider endpoint
- No reliance on external DNS inside the container
