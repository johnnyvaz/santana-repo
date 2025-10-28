---
title: "documentacao-tecnica"
category: "CLIENTES"
description: "Cliente: Equipe Santana  "
created: "2025-10-27"
updated: "2025-10-27"
---

# DOCUMENTAÇÃO TÉCNICA - PROJETO SANTANA

**Cliente:** Equipe Santana  
**Projeto:** Sistema Integrado de Atendimento, CRM e Notificações  
**Versão:** 1.0  
**Data:** 22 de Setembro de 2025  
**Desenvolvedor:** Johnny  
**Coordenador:** Tarcísio Santos (Jidu Marketing Digital)

---

## 📋 ÍNDICE

1. [Visão Geral da Arquitetura](#1-visão-geral-da-arquitetura)
2. [Infraestrutura](#2-infraestrutura)
3. [Componentes do Sistema](#3-componentes-do-sistema)
4. [Integrações](#4-integrações)
5. [Segurança](#5-segurança)
6. [Backup e Recuperação](#6-backup-e-recuperação)
7. [Monitoramento](#7-monitoramento)
8. [Manutenção](#8-manutenção)
9. [Troubleshooting](#9-troubleshooting)
10. [Apêndices](#10-apêndices)

---

## 1. VISÃO GERAL DA ARQUITETURA

### 1.1 Diagrama de Arquitetura

```
┌─────────────────────────────────────────────────────────────────┐
│                         CAMADA DE USUÁRIOS                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │   CLIENTES   │  │  ATENDENTES  │  │ PRESTADORES  │         │
│  │  (WhatsApp)  │  │  (Chatwoot)  │  │  (WhatsApp)  │         │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘         │
│         │                 │                  │                  │
└─────────┼─────────────────┼──────────────────┼──────────────────┘
          │                 │                  │
          │                 │                  │
┌─────────┼─────────────────┼──────────────────┼──────────────────┐
│         │    CAMADA DE APLICAÇÃO             │                  │
├─────────┼─────────────────┼──────────────────┼──────────────────┤
│         │                 │                  │                  │
│         ▼                 ▼                  │                  │
│  ┌──────────────────────────────────┐       │                  │
│  │     WHATSAPP BUSINESS API        │       │                  │
│  │    (Integração Oficial)          │       │                  │
│  └────────────┬─────────────────────┘       │                  │
│               │                              │                  │
│               ▼                              │                  │
│  ┌──────────────────────────────────┐       │                  │
│  │         CHATWOOT                 │◄──────┘                  │
│  │  (Plataforma de Atendimento)     │                          │
│  └────────────┬─────────────────────┘                          │
│               │                                                 │
│               ▼                                                 │
│  ┌──────────────────────────────────┐                          │
│  │            n8n                   │                          │
│  │  (Automação e Orquestração)      │                          │
│  └────────┬─────────────┬───────────┘                          │
│           │             │                                       │
│           ▼             ▼                                       │
│  ┌────────────┐  ┌──────────────────┐                          │
│  │   ODOO     │  │  NOTIFICAÇÕES    │                          │
│  │   CRM      │  │  (WhatsApp/SMS)  │                          │
│  └────────────┘  └──────────────────┘                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
          │                                                       
          │                                                       
┌─────────┼───────────────────────────────────────────────────────┐
│         │         CAMADA DE DADOS                               │
├─────────┼───────────────────────────────────────────────────────┤
│         │                                                       │
│         ▼                                                       │
│  ┌──────────────────────────────────┐                          │
│  │       POSTGRESQL                 │                          │
│  │  (Banco de Dados Principal)      │                          │
│  └──────────────────────────────────┘                          │
│                                                                 │
│  ┌──────────────────────────────────┐                          │
│  │         REDIS                    │                          │
│  │  (Cache e Filas)                 │                          │
│  └──────────────────────────────────┘                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
          │
          │
┌─────────┼───────────────────────────────────────────────────────┐
│         │      CAMADA DE INFRAESTRUTURA                         │
├─────────┼───────────────────────────────────────────────────────┤
│         │                                                       │
│         ▼                                                       │
│  ┌──────────────────────────────────┐                          │
│  │      SERVIDOR VPS                │                          │
│  │   Ubuntu 22.04 LTS               │                          │
│  │   4GB RAM / 2 vCPUs / 80GB SSD   │                          │
│  └──────────────────────────────────┘                          │
│                                                                 │
│  ┌──────────────────────────────────┐                          │
│  │      NGINX (Reverse Proxy)       │                          │
│  │      SSL/TLS (Let's Encrypt)     │                          │
│  └──────────────────────────────────┘                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 1.2 Stack Tecnológico

| Camada | Tecnologia | Versão | Propósito |
|--------|-----------|--------|-----------|
| **Sistema Operacional** | Ubuntu Server | 22.04 LTS | Base do servidor |
| **Proxy Reverso** | Nginx | 1.18+ | Roteamento e SSL |
| **Banco de Dados** | PostgreSQL | 14+ | Armazenamento principal |
| **Cache** | Redis | 6.2+ | Cache e filas |
| **CRM** | Odoo | 17 | Gestão de clientes e eventos |
| **Atendimento** | Chatwoot | 3.0+ | Interface de chat |
| **Automação** | n8n | 1.0+ | Workflows e integrações |
| **Linguagem** | Python | 3.8+ | Backend Odoo |
| **Linguagem** | Node.js | 18+ | n8n e Chatwoot |
| **Containerização** | Docker | 24+ | Isolamento de aplicações |

---

## 2. INFRAESTRUTURA

### 2.1 Especificações do Servidor

**Servidor VPS**
- **Provedor:** [A definir - DigitalOcean/Vultr/AWS]
- **Localização:** São Paulo, Brasil
- **Especificações:**
  - CPU: 2 vCPUs
  - RAM: 4GB
  - Armazenamento: 80GB SSD
  - Largura de Banda: Ilimitada
  - IP: [A definir]

**Sistema Operacional**
- Ubuntu Server 22.04 LTS
- Kernel: 5.15+
- Timezone: America/Sao_Paulo

### 2.2 Estrutura de Diretórios

```
/opt/
├── chatwoot/              # Instalação do Chatwoot
│   ├── docker-compose.yml
│   ├── .env
│   └── data/
├── n8n/                   # Instalação do n8n
│   ├── docker-compose.yml
│   ├── .env
│   └── data/
├── odoo/                  # Instalação do Odoo
│   ├── odoo.conf
│   ├── addons/
│   ├── custom-addons/
│   └── data/
└── backups/               # Backups automáticos
    ├── daily/
    ├── weekly/
    └── monthly/

/var/log/
├── chatwoot/
├── n8n/
├── odoo/
└── nginx/

/etc/nginx/
├── sites-available/
│   ├── chatwoot.conf
│   ├── n8n.conf
│   └── odoo.conf
└── sites-enabled/
```

### 2.3 Domínios e Subdomínios

| Serviço | Subdomínio | Porta Interna | SSL |
|---------|-----------|---------------|-----|
| CRM Odoo | crm.santana.com.br | 8069 | ✅ |
| Chatwoot | chat.santana.com.br | 3000 | ✅ |
| n8n | n8n.santana.com.br | 5678 | ✅ |
| API | api.santana.com.br | 8080 | ✅ |

### 2.4 Portas e Firewall

**Portas Abertas:**
```bash
22/tcp   - SSH (acesso restrito por IP)
80/tcp   - HTTP (redirect para HTTPS)
443/tcp  - HTTPS
```

**Configuração UFW:**
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow from [IP_AUTORIZADO] to any port 22
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

---

## 3. COMPONENTES DO SISTEMA

### 3.1 Chatwoot

**Descrição:** Plataforma open-source de atendimento ao cliente

**Instalação via Docker:**
```yaml
# /opt/chatwoot/docker-compose.yml
version: '3'

services:
  postgres:
    image: postgres:14
    restart: always
    volumes:
      - ./data/postgres:/var/lib/postgresql/data
    environment:
      - POSTGRES_DB=chatwoot
      - POSTGRES_USER=chatwoot
      - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}

  redis:
    image: redis:6-alpine
    restart: always
    command: redis-server --requirepass ${REDIS_PASSWORD}
    volumes:
      - ./data/redis:/data

  chatwoot:
    image: chatwoot/chatwoot:latest
    restart: always
    depends_on:
      - postgres
      - redis
    ports:
      - "3000:3000"
    environment:
      - RAILS_ENV=production
      - SECRET_KEY_BASE=${SECRET_KEY_BASE}
      - POSTGRES_HOST=postgres
      - POSTGRES_USERNAME=chatwoot
      - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
      - REDIS_URL=redis://redis:6379
      - REDIS_PASSWORD=${REDIS_PASSWORD}
      - FRONTEND_URL=https://chat.santana.com.br
    volumes:
      - ./data/storage:/app/storage
```

**Variáveis de Ambiente:**
```bash
# /opt/chatwoot/.env
POSTGRES_PASSWORD=senha_segura_postgres
REDIS_PASSWORD=senha_segura_redis
SECRET_KEY_BASE=chave_secreta_gerada
FRONTEND_URL=https://chat.santana.com.br
```

**Configuração do Inbox WhatsApp:**
1. Acessar Chatwoot Admin
2. Settings → Inboxes → Add Inbox
3. Selecionar "WhatsApp"
4. Configurar WhatsApp Business API
5. Webhook URL: `https://chat.santana.com.br/webhooks/whatsapp`

**APIs Importantes:**
- Criar conversa: `POST /api/v1/accounts/{account_id}/conversations`
- Enviar mensagem: `POST /api/v1/accounts/{account_id}/conversations/{id}/messages`
- Webhook: `POST /webhooks/whatsapp`

### 3.2 n8n

**Descrição:** Plataforma de automação de workflows

**Instalação via Docker:**
```yaml
# /opt/n8n/docker-compose.yml
version: '3'

services:
  n8n:
    image: n8nio/n8n:latest
    restart: always
    ports:
      - "5678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=${N8N_USER}
      - N8N_