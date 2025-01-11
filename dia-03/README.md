# Dia 03

O desafio consiste em criar uma imagem docker para o projeto [Giropops Senhas](https://github.com/badtuxx/giropops-senhas) utilizando como base as imagens da [Chainguard](https://images.chainguard.dev/).

Requisitos:

    - Utilizar como base as imagens da Chainguard
    - Imagem de tamanho reduzido
    - Testar para vulnerabilidades

## Build

Realizar o build da imagem docker 

```bash
docker image build --tag schleuss/giropops-senhas-chainguard .
```

## Validações

Verificar o tamanho de imagem gerado.

```bash
docker image ls schleuss/giropops-senhas-chainguard
REPOSITORY                            TAG       IMAGE ID       CREATED          SIZE
schleuss/giropops-senhas-chainguard   latest    f149855edc9a   12 minutes ago   66.2MB
```

Verificar a imagem utilizando o trivy

```bash
λ trivy image schleuss/giropops-senhas-chainguard
2025-01-11T17:11:36-03:00       INFO    [vuln] Vulnerability scanning is enabled
2025-01-11T17:11:36-03:00       INFO    [secret] Secret scanning is enabled
2025-01-11T17:11:36-03:00       INFO    [secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-01-11T17:11:36-03:00       INFO    [secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-01-11T17:11:37-03:00       INFO    Detected OS     family="wolfi" version="20230201"
2025-01-11T17:11:37-03:00       INFO    [wolfi] Detecting vulnerabilities...    pkg_num=23
2025-01-11T17:11:37-03:00       INFO    Number of language-specific files       num=1
2025-01-11T17:11:37-03:00       INFO    [python-pkg] Detecting vulnerabilities...

schleuss/giropops-senhas-chainguard (wolfi 20230201)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```
