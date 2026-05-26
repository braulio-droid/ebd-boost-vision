# Deploy passo a passo

Receita do zero até a URL pública. ~10 minutos.

## Pré-requisitos

1. Conta no [GitHub](https://github.com/signup) (gratuita)
2. Conta no [Vercel](https://vercel.com/signup) — pode logar com GitHub (gratuita)
3. (Opcional) [Git](https://git-scm.com) instalado localmente

---

## Caminho A — pelo navegador (sem Git)

### 1. Criar repositório no GitHub

1. Acesse [github.com/new](https://github.com/new)
2. Nome: `ebd-boost-vision`
3. Marque **Private** se quiser proteger
4. Marque **Add README**
5. Clique **Create repository**

### 2. Subir os arquivos

1. No novo repo, clique **Add file → Upload files**
2. Arraste TODA a pasta `ebd-boost-vision/` (com index.html, README.md, vercel.json, .gitignore, CHANGELOG.md, docs/)
3. Commit message: `EBD Boost Vision MVP v3`
4. Clique **Commit changes**

### 3. Conectar Vercel

1. Acesse [vercel.com/new](https://vercel.com/new)
2. Faça login com GitHub se ainda não fez
3. Em **Import Git Repository** procure `ebd-boost-vision`
4. Clique **Import**
5. Em **Configure Project**:
   - **Framework Preset**: `Other`
   - **Root Directory**: `./` (default)
   - **Build Command**: deixe VAZIO
   - **Output Directory**: deixe VAZIO
   - **Install Command**: deixe VAZIO
6. Clique **Deploy**

Em ~30s aparece o "Congratulations" com a URL pública (ex: `https://ebd-boost-vision-xyz.vercel.app`). Pronto.

---

## Caminho B — terminal (recomendado para quem tem Git)

```bash
# clone a pasta do MVP em qualquer lugar
cd ebd-boost-vision

# inicializa Git
git init
git add .
git commit -m "EBD Boost Vision MVP v3"
git branch -M main

# crie o repo no GitHub primeiro pelo site (vazio, sem README)
# copie a URL HTTPS, exemplo:
git remote add origin https://github.com/SEU-USUARIO/ebd-boost-vision.git
git push -u origin main
```

Vercel:

```bash
# instala CLI (opcional)
npm i -g vercel

# dentro da pasta
vercel
# responda às perguntas, primeira vez:
#   Set up and deploy? [Y/n] Y
#   Which scope? <sua conta>
#   Link to existing project? [y/N] N
#   Project name: ebd-boost-vision
#   In which directory is your code? ./
#   Want to modify settings? [y/N] N

# deploy de produção
vercel --prod
```

URL final aparece no console.

---

## Domínio próprio (opcional)

Tem `ebd.sellers.com.br` ou similar? No painel do Vercel:

1. Projeto → **Settings → Domains**
2. Cole o domínio e clique **Add**
3. Vercel mostra os registros DNS para apontar (CNAME ou A)
4. No seu provedor de DNS (Registro.br, GoDaddy, Cloudflare, etc) crie os registros
5. Aguarde propagação (~10 min) — Vercel emite SSL automático

---

## Atualizar depois

### Pelo site GitHub

1. Abra o repo
2. Clique em `index.html`
3. Clique no lápis para editar
4. Faça a mudança e commit
5. Vercel detecta e faz redeploy em ~30s

### Pelo terminal

```bash
# edita o arquivo localmente
git add index.html
git commit -m "Ajuste no Briefing"
git push
# Vercel redeploy automático
```

---

## Branch de teste (recomendado)

Antes de mudar a versão de produção, teste em branch separada:

```bash
git checkout -b feature/nova-aba
# edita arquivos
git add . && git commit -m "Nova aba"
git push -u origin feature/nova-aba
```

Vercel cria automaticamente um **Preview URL** específico para a branch (ex: `ebd-boost-vision-git-feature-nova-aba.vercel.app`). Use esse link para testar com os vendedores antes de merge para `main`.

Quando aprovado:

```bash
git checkout main
git merge feature/nova-aba
git push
```

---

## Variáveis sensíveis

**Não precisa.** O MVP não tem chaves de API privadas, tudo é client-side e usa serviços gratuitos com CORS aberto.

Se algum dia integrar Google Maps API paga ou backend:
- Vercel → **Settings → Environment Variables**
- Adicione `NEXT_PUBLIC_*` para client ou normais para server-side

---

## Custos

Vercel **Hobby plan**: gratuito até 100GB de banda/mês. Suficiente para uma equipe inteira da EBD.

Se passar disso, mudar para **Pro** (~$20/mês) — improvável para essa carga de uso.
