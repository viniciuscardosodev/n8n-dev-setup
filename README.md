# n8n — Instância local de teste (Docker)

Pronto para subir com Docker Compose em poucos passos.

## Requisitos
- Docker e Docker Compose (v2)
- Porta `5678` livre (pode mudar no `.env`)

## Como subir
```bash
docker compose up -d
```
Acesse: http://localhost:5678 e crie o usuário inicial (owner).

## Como parar
```bash
docker compose down
```

## Onde ficam os dados
- Volume local: `./n8n_data` (inclui banco SQLite, credenciais, workflows etc.)

## Atualizar versão
```bash
docker compose pull
docker compose up -d
```

## Customizações comuns
- **Porta**: altere `N8N_PORT` no `.env`.
- **Fuso horário**: `TZ` e `GENERIC_TIMEZONE` no `.env`.
- **URL pública/Webhooks**: ajuste `N8N_PUBLIC_URL` e `WEBHOOK_URL` se usar proxy ou acessar via IP/rede.
- **Chave de criptografia** (`N8N_ENCRYPTION_KEY`): já gerada para uso imediato, troque se desejar.
- **Autenticação adicional** (opcional): você pode habilitar Basic Auth adicionando no `.env`:
  ```
  N8N_BASIC_AUTH_ACTIVE=true
  N8N_BASIC_AUTH_USER=admin
  N8N_BASIC_AUTH_PASSWORD=troque-esta-senha
  ```
  > Observação: o n8n possui User Management via UI; o Basic Auth é apenas uma camada extra simples.

## Observações
- Este setup usa o **SQLite** embutido para testes. Em produção, prefira **PostgreSQL**.
- O container é baseado em `n8nio/n8n:latest`. Para travar a versão, altere o `Dockerfile`.
