# Passo a passo — Subir o EBD Boost Vision no GitHub

Guia visual completo, sem precisar terminal nem Git. ~10 minutos do zero até a URL pública.

---

## ⚙️ Preparação (1 minuto)

### O que você precisa
- ✅ O arquivo `ebd-boost-vision.zip` baixado
- ✅ Um navegador (Chrome, Edge, Firefox, Safari)
- ✅ Conta no GitHub (vou explicar como criar abaixo)
- ✅ Conta no Vercel (vou explicar como criar abaixo)

### Descompactar o ZIP
1. Localize o arquivo `ebd-boost-vision.zip` no seu computador
2. Clique com botão direito → **Extrair tudo** (Windows) ou **Abrir** (Mac)
3. Vai criar uma pasta `ebd-boost-vision/` com 7 arquivos dentro:
   - `index.html`
   - `README.md`
   - `DEPLOY.md`
   - `CHANGELOG.md`
   - `PASSO_A_PASSO_GITHUB.md` ← este arquivo
   - `vercel.json`
   - `.gitignore`
   - `docs/` (subpasta com 2 arquivos)

Deixe essa pasta aberta — vamos precisar arrastar tudo daqui.

---

## 🔑 Parte 1 — Criar conta no GitHub (pule se já tem)

1. Abra https://github.com/signup
2. Preencha:
   - **Email** → seu email corporativo
   - **Password** → senha forte
   - **Username** → algo como `seu-nome` ou `ebd-sellers` (será visível na URL)
3. Confirme o email (vai chegar um código)
4. Pronto. **Não precisa pagar nada.**

---

## 📦 Parte 2 — Criar o repositório (1 minuto)

1. Faça login em https://github.com
2. No canto superior direito, clique no **➕** e escolha **New repository**

   ![passo](https://docs.github.com/assets/cb-11427/mw-1440/images/help/repository/repo-create-global-nav-update.webp)

3. Preencha:

   | Campo | Valor |
   |---|---|
   | **Owner** | seu usuário (já vem preenchido) |
   | **Repository name** | `ebd-boost-vision` |
   | **Description** | `Copiloto de campo do vendedor EBD` |
   | **Public / Private** | **Private** (recomendado) |
   | **Add a README file** | ❌ **DEIXE DESMARCADO** (já temos um) |
   | **Add .gitignore** | ❌ DEIXE DESMARCADO |
   | **Choose a license** | None |

4. Clique no botão verde **Create repository** no final

> Se aparecer **"Initialize this repository"**, deixe TUDO desmarcado. Queremos um repo vazio.

---

## 📤 Parte 3 — Subir os arquivos (3 minutos)

Você vai ver uma tela com várias opções. Não use o terminal. Use o **uploading an existing file**.

1. Procure o link **"uploading an existing file"** (em azul, no meio da tela)
   - Ou acesse diretamente: `https://github.com/SEU-USUARIO/ebd-boost-vision/upload/main`

2. Vai aparecer uma área de drop chamada **"Drag files here to add them to your repository"**

3. **Abra duas janelas lado a lado**: a pasta `ebd-boost-vision/` (descompactada) e o navegador

4. **Selecione TODOS os arquivos e a subpasta `docs/`** dentro da pasta `ebd-boost-vision/`:
   - `index.html`
   - `README.md`
   - `DEPLOY.md`
   - `CHANGELOG.md`
   - `PASSO_A_PASSO_GITHUB.md`
   - `vercel.json`
   - `.gitignore` (se não aparecer, ative "Mostrar arquivos ocultos" no explorador)
   - `docs/` (a pasta inteira)

   > ⚠️ **NÃO arraste a pasta `ebd-boost-vision/` inteira.** Arraste o **conteúdo** dela. Senão o GitHub cria uma subpasta extra e o Vercel não vai achar o `index.html`.

5. **Arraste tudo** para a área cinza pontilhada do GitHub

6. Aguarde a barra verde "Uploading..." chegar em 100%

7. Lá embaixo, no campo de **commit message**, escreva: `EBD Boost Vision MVP v3`

8. Clique no botão verde **Commit changes**

9. ✅ Pronto. Agora você verá os arquivos listados na página principal do repo.

---

## 🚀 Parte 4 — Publicar no Vercel (3 minutos)

### Criar conta Vercel (pule se já tem)

1. Abra https://vercel.com/signup
2. Clique em **Continue with GitHub** (mais rápido — usa o login do GitHub)
3. Autorize o Vercel a acessar suas informações do GitHub
4. Escolha plano **Hobby** (gratuito)
5. Pronto, está logado

### Importar o repositório

1. No painel do Vercel (vercel.com/dashboard), clique em **Add New… → Project**

2. Vai aparecer uma lista de repositórios do GitHub. Procure **`ebd-boost-vision`**.

   - Se NÃO aparecer: clique em **Adjust GitHub App Permissions** e libere acesso a esse repo.

3. Ao lado do `ebd-boost-vision`, clique no botão **Import**

4. Tela **"Configure Project"** — vai aparecer:

   | Campo | O que fazer |
   |---|---|
   | **Project Name** | deixe `ebd-boost-vision` |
   | **Framework Preset** | mude para **Other** |
   | **Root Directory** | deixe `./` (raiz) |
   | **Build and Output Settings** | clique para expandir e **deixe os 3 campos VAZIOS** (Build Command, Output Directory, Install Command) |
   | **Environment Variables** | não preencha nada |

5. Clique no botão preto **Deploy** no canto inferior direito

6. Aguarde ~30 segundos. Vai aparecer uma animação de confete 🎉 e a URL pública:
   - Algo como `https://ebd-boost-vision-abc123.vercel.app`

7. Clique em **Continue to Dashboard** ou direto na URL para abrir o painel ao vivo

---

## ✅ Pronto! O que fazer agora

### Compartilhar com a equipe
A URL é pública por padrão (mesmo o repo sendo privado). Mande para o Thomaz e os vendedores testarem.

### Customizar o link (opcional)
1. No painel do Vercel, abra o projeto
2. Vá em **Settings → Domains**
3. Clique em **Edit** ao lado do domínio `.vercel.app`
4. Mude para algo mais bonito como `ebd-vendedor.vercel.app`

### Ligar domínio próprio (opcional, se a Sellers tem subdomínio livre)
1. **Settings → Domains**
2. Cole `ebd.sellers.com.br` (ou outro)
3. O Vercel mostra DNS para apontar
4. Configure no provedor de DNS da Sellers
5. SSL automático em ~10 minutos

---

## 🔄 Como atualizar depois

Sempre que quiser mudar o painel:

### Caminho fácil (pelo GitHub web)
1. Abra `https://github.com/SEU-USUARIO/ebd-boost-vision`
2. Clique em `index.html`
3. Clique no ícone de lápis (✏️) no canto superior direito do código
4. Edite o que precisar
5. Vá ao final, escreva mensagem de commit (ex: `Corrige bug do mapa`)
6. Clique **Commit changes**
7. ⏰ O Vercel detecta sozinho e em ~30s atualiza a URL — não precisa fazer mais nada

### Caminho seguro (com branch de teste)
Se a equipe está usando, não mude direto:

1. Na página do repo, ao lado de **main**, clique no dropdown
2. Digite um nome novo, ex: `teste-mapa`
3. Clique em **Create branch: teste-mapa**
4. Edite o arquivo nessa nova branch
5. O Vercel gera uma URL separada para a branch (ex: `ebd-boost-vision-git-teste-mapa.vercel.app`)
6. Teste com 1 vendedor
7. Quando aprovado: na página do repo, clique **Pull Requests → New** → da branch `teste-mapa` para `main` → **Merge**
8. Aí sim atualiza a URL principal

---

## ❓ Problemas comuns

### "Site Not Found" depois do deploy
- Verifique se o `index.html` está na RAIZ do repo (não dentro de uma subpasta)
- Se está dentro de subpasta, mova para a raiz e faça novo commit

### Vercel diz "Build failed"
- Vá em **Settings → General → Build & Development Settings**
- Confirme: **Framework Preset = Other**, todos os 3 campos de build vazios

### Repositório aparece privado mas a URL Vercel é pública
- Isso é **normal e correto**. O repo guarda o código (privado), o Vercel hospeda a versão renderizada (pública). Quem acessa a URL do Vercel não vê o código.

### Não consigo encontrar o `.gitignore`
- No Windows: Explorador → **Exibir → Itens ocultos**
- No Mac: na pasta, aperte `Cmd + Shift + .`

### Os arquivos foram subidos mas o painel não carrega
- Abra o Console do navegador (F12) → aba Console
- Provavelmente algum CDN está bloqueado pela rede da empresa
- O MVP usa: cdn.tailwindcss.com, unpkg.com, cdn.jsdelivr.net, cdnjs.cloudflare.com — todos devem estar liberados

### Recarrega mas não atualiza
- Cache do navegador. Aperte **Ctrl + Shift + R** (Windows) ou **Cmd + Shift + R** (Mac) para forçar reload

---

## 🆘 Ajuda

Qualquer dúvida no processo, abra um issue no próprio GitHub:
1. `https://github.com/SEU-USUARIO/ebd-boost-vision/issues`
2. **New issue** → descreva o problema com print

---

**Pronto!** Em 10 minutos o EBD Boost Vision está rodando online, com SSL, em URL pública, atualizando sozinho a cada commit.
