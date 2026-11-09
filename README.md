# Dindi

App de controle financeiro pessoal (mascote: Mimo). HTML único, sem build.
Backend: Supabase (Auth + Postgres com RLS). Hospedagem: Netlify.

## Estrutura
- `public/index.html` — o app inteiro (é o que vai ao ar)
- `supabase/` — SQL a rodar no SQL Editor do Supabase, **em ordem**
- `netlify.toml` — publica só `public/` e define cabeçalhos de segurança

## Supabase (uma vez)
1. SQL inicial do projeto (8 tabelas + RLS) — já executado.
2. `supabase/001_auth.sql` — login por usuário.
3. `supabase/002_preparar_sincronizacao.sql` — saldo inicial e permissões.
4. Authentication → URL Configuration: em **Site URL** e **Redirect URLs** coloque o endereço do Netlify
   (e `http://localhost:5500` para testes locais).
5. Authentication → Providers → Email: tamanho mínimo da senha = 8.

## Deploy
Netlify → Add new site → Import from Git → escolha este repositório. Deploy automático a cada push.

## Segurança
- Só a chave **publishable** do Supabase está no código (ela é pública por definição).
- **Nunca** coloque a `service_role` no código nem no repositório.
- Não suba backups JSON nem scripts com dados financeiros pessoais.
