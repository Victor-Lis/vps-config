
# 🚀 VPS Config — Configurações rápidas para seu VPS com Docker

![status: ready](https://img.shields.io/badge/status-ready-green) ![docker](https://img.shields.io/badge/docker-ready-blue) ![shield](https://img.shields.io/badge/setup-easy-orange)

Bem-vindo!  
Este repositório reúne templates e configurações para subir serviços úteis em um VPS com Docker Compose. Ideal para testar, recuperar ou provisionar pequenos ambientes.

---

## 🧩 Serviços incluídos

### 🗄️ Postgres (postgres:16)
Banco relacional. Usado principalmente pelo n8n. Volume: `./postgres/data`

---

### 🤖 n8n (n8nio/n8n)
Plataforma de automação *low-code*. Volume: `./n8n`

---

### 🔌 MQTT (eclipse-mosquitto:latest)
Broker leve para mensageria/IoT. Volume: `./mqtt`

---

### 🧭 Portainer (portainer/portainer-ce:latest)
Painel web para gerenciar containers. Volume: `./portainer`

---

## 📂 Estrutura do repositório

- `docker-compose.yml` — arquivo principal
- `mqtt/` — dados e configuração do Mosquitto
- `n8n/` — dados do n8n
- `portainer/` — dados do Portainer
- `postgres/` — dados do Postgres
- `.gitignore` — ignora diretórios de dados
- `README.md`

> Observação: diretórios de dados são ignorados para evitar commits de dados sensíveis.

---

## ⚙️ Pré-requisitos

- `git`
- `docker`
- `docker-compose`

---

## ⚡ Início rápido

1) Clone o repositório:
```bash
git clone <url-do-repositorio>
cd vps-config
```

2) Ajuste as configurações:

- Revise `docker-compose.yml`.
- Atualize portas, volumes e variáveis de ambiente (senhas, etc.).

3) Suba os serviços:
```bash
docker-compose up -d
```

---

## 🛠️ Comandos úteis

Ver logs (ao vivo):
```bash
docker-compose logs -f <serviço>
```

Recriar serviço (forçando rebuild):
```bash
docker-compose up -d --force-recreate --build <serviço>
```

Parar / iniciar serviço:
```bash
docker-compose stop <serviço>
docker-compose start <serviço>
```

---

## 💾 Backup e restauração (ex.: Postgres)

1. Pare o serviço:
```bash
docker-compose stop postgres
```

2. Substitua `./postgres/data` pelo backup (copiar/untar).

3. Reinicie:
```bash
docker-compose up -d postgres
```

---

## 🔒 Boas práticas e segurança

- Nunca comite segredos no `docker-compose.yml`. Use `.env` (e adicione ao `.gitignore`) ou gerenciadores de secret.
- Faça backups regulares dos volumes (`postgres/data`, `n8n/`).
- Em produção, prefira volumes gerenciados/externalizados e rotinas de backup robustas.

---

## ✉️ Contribuições & suporte

Abra uma issue ou envie um pull request.  
Se quiser, descreva portas/volumes/serviços e eu adapto o `docker-compose.yml`.

---

## 👤 Autor

**Victor Lis Bronzo**  
[LinkedIn](https://www.linkedin.com/in/victor-lis-bronzo) • [GitHub](https://github.com/Victor-Lis)
