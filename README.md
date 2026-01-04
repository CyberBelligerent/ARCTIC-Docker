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

## Provider Usage

**If using http / IP only, this can be skipped**
If using HTTPs, odds are, you're using DNS rather than IP address. To make sure ARCTIC can talk to your provider over DNS ensure to add the following setting inside of your docker-compose.yml file:
```yml
  arctic-app:
    extra_hosts:
      - "{DNS_NAME}:{IP}"
```

Then, when connecting to a providers endpoint, use the DNS name instead of the IP address!
