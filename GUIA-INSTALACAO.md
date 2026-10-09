# Painel administrativo — implantação

**Estado:** código preparado; o acesso ainda NÃO está ativo até configurar o Supabase.

## 1. Criar banco dedicado
Crie um projeto Supabase específico para a associação. No SQL Editor execute `supabase/schema.sql`. Não use o banco do GESTASSP.

## 2. Criar a conta administrativa
Em Supabase > Authentication > Users, crie o usuário administrativo (convite por e-mail, se disponível). Copie o UUID e execute, substituindo o exemplo pelo ID real:

```sql
insert into public.portal_admins (user_id, role) values ('UUID-DO-USUARIO', 'admin');
```

Não disponibilize as credenciais por mensagens públicas. Não habilite cadastro livre de usuários.

## 3. Conectar o site
Em Supabase > Project Settings > API, copie `Project URL` e a chave **pública** `anon`/`publishable`. Insira em `config.js`, nunca a `service_role` ou uma secret key. Faça commit no GitHub dos arquivos da pasta do site, inclusive `admin.html`, `admin.js`, `portal-publico.js`, `config.js` e `supabase/schema.sql`.

## 4. Testar
Abra `https://associacao-lagoa-de-santana.vercel.app/admin.html`, entre com a conta autorizada, cadastre parceria em rascunho, publique depois de conferir, envie um PDF público de teste sem dados sensíveis e confira sua exibição em `transparencia.html`.

## 5. Cuidados relevantes
- A publicação de PDFs é pública mesmo quando o cadastro está em rascunho. Não suba um PDF até ele estar aprovado para divulgação.
- Todo lançamento financeiro deve corresponder a dados e comprovantes reais.
- Mantenha backups, revise permissões e implemente rotina de conferência antes da utilização oficial.
- O arquivo `dados/transparencia.json` ainda contém o comprovante de CNPJ existente; carregue essa pasta para não apresentar erro.
- Documentos do estatuto e da ata originais contêm CPFs/assinaturas de terceiros e não devem ser publicados integralmente sem revisão.
- Ao atualizar o GitHub, não exponha senhas.

## Revisão de permissões (09/10/2026)
- O esquema agora impede que perfis `editor` publiquem registros; publicação requer `admin`.
- Upload de PDF ao bucket `portal-publico` está restrito a `admin`, pois os arquivos ficam acessíveis por URL direta imediatamente.
- NÃO use esse bucket para documentos sigilosos ou rascunhos com dados pessoais. Uma futura revisão implementará armazenamento privado e publicação segura.
