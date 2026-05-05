# Painel Azilab

Sistema de painéis operacionais integrado com Supabase.

## Como usar

### Cliente (Estefânia)

URL: `https://painel-azilab.vercel.app/?token=token_5031264b-79b8-4baf-b5bc-928c0b3ac1d4`

Substitua o token pelo token do cliente.

### Admin (você)

Vá em Supabase e:

1. **Para criar novo cliente:**
```sql
INSERT INTO clientes (slug, nome, projeto, token_acesso)
VALUES ('slug-cliente', 'Nome Cliente', 'Projeto', 'token_' || gen_random_uuid()::text)
RETURNING slug, token_acesso;
```

2. **Para adicionar fases:** Use a interface do Supabase ou SQL direto

3. **Para adicionar tarefas:** Igual, via Supabase

## Deploy no Vercel

1. Cria um repositório Git:
```bash
cd painel-azilab
git init
git add .
git commit -m "Initial commit"
```

2. Push pra GitHub (cria repo em github.com)
```bash
git remote add origin https://github.com/seu-usuario/painel-azilab.git
git branch -M main
git push -u origin main
```

3. Vai em vercel.com, clica "Import Project", seleciona o repositório

4. Na configuração, deixa como está (é site estático)

5. Deploy!

URL final será tipo: `https://painel-azilab.vercel.app`

## Estrutura do banco

- **clientes**: dados dos clientes
- **fases**: fases de cada projeto
- **tarefas**: tarefas dentro de cada fase
- **materiais**: PDFs, links, etc de cada fase
- **biblioteca**: materiais globais do cliente

## Notas

- Cada cliente tem uma URL única com token
- O token é privado, só compartilha com o cliente
- Dados persistem no Supabase
- Atualizações são em tempo real

## Suporte

Qualquer coisa, edita direto no Supabase e depois mexe na aplicação conforme necessário.
