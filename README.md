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
