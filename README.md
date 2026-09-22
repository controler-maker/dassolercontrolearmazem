# Dassoler Agronegócios — Controle Operacional

Sistema de armazém para originação, classificação, exportação, diesel, embalagens e marmitas.

> 📘 **Nunca usou GitHub?** Siga o passo a passo completo e gratuito em [`COMO-PUBLICAR-NO-GITHUB.md`](./COMO-PUBLICAR-NO-GITHUB.md).
> 
> 🟢 **Quer só usar o site no dia a dia sem bugs?** Leia [`COMO-USAR.md`](./COMO-USAR.md) — é o guia mais simples possível.

## Acesso do administrador

- **Usuário:** `DASSOLER`
- **Senha:** `Dassoler@123.`

O usuário também aceita `dassoler` (minúsculas). A senha oficial leva o ponto final.

## Como publicar no GitHub

1. Crie um repositório novo no GitHub (pode ser privado).
2. No computador, na pasta do projeto:

```bash
git init
git add .
git commit -m "Sistema operacional Dassoler"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
git push -u origin main
```

Não envie o arquivo `.env` (ele já está no `.gitignore`). Use o `.env.example` como modelo.

## Como rodar localmente

Requisitos: Node.js 20+, PostgreSQL.

```bash
cp .env.example .env
# Ajuste DATABASE_URL no .env
npm install
npx drizzle-kit push
npm run build
npm run start
```

Abra `http://localhost:3000` e entre com **DASSOLER** / **Dassoler@123.**

## Publicar na Vercel (opcional)

1. Importe o repositório na Vercel.
2. Configure `DATABASE_URL` apontando para o PostgreSQL de produção.
3. Faça o deploy. O login usa cookie seguro em HTTPS.

## O que o sistema controla

- Recebimento de produtores (grão, variedade, pesos, classificação MT)
- Carregamentos de exportação (romaneio automático, bags/sacas)
- Pesagens avulsas
- Relatórios por produtor, diesel e marmitas
- Diesel S500 e S-10 (entrada soma no saldo, uso desconta)
- Bags e sacas por tamanho
- Pedidos de marmitas (Matriz/Filial, P/M/G)

## Como corrigir um lançamento

Qualquer registro pode ser **editado** ou **excluído** na própria aba. Os totais e o estoque são recalculados automaticamente após salvar.

## Precisão das contagens

- Peso comercial do produtor = líquido classificado, se houver classificação; senão, o peso neto da balança.
- Relatório do produtor soma apenas as cargas daquele nome/código, com filtro opcional de grão.
- Diesel: recebimento entra no tanque do tipo (S500 ou S-10); abastecimento sai do mesmo tipo.
- Marmitas: totais por unidade e tamanho P/M/G.

Se um número parecer errado, abra o lançamento, ajuste e salve — o relatório acompanha na hora.
