# Ativação do painel administrativo

1. Banco criado: manter o projeto Supabase exclusivo da associação. Não execute `schema.sql` novamente.
2. No SQL Editor, execute somente `supabase/MIGRACAO-SEGURANCA.sql`. Verifique sucesso.
3. No GitHub, carregue os arquivos da pasta do site na raiz do repositório, incluindo `config.js`, `admin.html`, `admin.js`, `portal-publico.js`, `transparencia.html`, `dados/`, `documentos/`, `imagens/`, `index.html` e `logo.png`. Preserve as subpastas.
4. Aguarde o deploy Ready na Vercel. Teste a página pública `/transparencia.html` e o login em `/admin.html` com o usuário autorizado.
5. Faça um teste com documento PDF sem dados pessoais: cadastrar rascunho, verificar que não aparece no portal, publicar, conferir que aparece, retirar publicação e conferir que deixa de aparecer. Arquivos já baixados por terceiros não podem ser revogados.
6. Revise RLS, logs e teste com usuário anônimo e editor antes de uso real. Não envie chaves secretas nem credenciais ao GitHub.

A URL e a chave publishable estão em `config.js`; não são segredo, mas a segurança depende de RLS e políticas de Storage.
