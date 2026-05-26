# EBD Boost Vision

Copiloto de campo do vendedor EBD — Sellers. MVP HTML estático: roda 100% no navegador, sem backend.

## O que é

Painel web que ajuda vendedor e supervisor da EBD a:

- Planejar rota do dia (drag-and-drop)
- Navegar no Google Maps com check-in/check-out automático
- Receber sugestão inteligente de produtos por cliente, cruzando:
  - Histórico do cliente
  - Promoções do jornalzinho (PDF do mês)
  - Campanhas vigentes
  - Clientes do mesmo ramo (ex: outros mercadinhos)
- Recuperar clientes 90+ sem comprar
- Acompanhar progresso da equipe (visão supervisor)

Documentação completa em [`docs/COMO_USAR.md`](docs/COMO_USAR.md) e [`docs/PLANILHAS.md`](docs/PLANILHAS.md).

## Como rodar localmente

Não precisa Node, npm ou build. Basta abrir `index.html` no navegador:

```bash
# qualquer servidor estático funciona
python3 -m http.server 8000
# ou
npx serve .
```

Acesse `http://localhost:8000`.

## Deploy no Vercel (recomendado)

### Passo 1 — Subir no GitHub

```bash
git init
git add .
git commit -m "EBD Boost Vision MVP v3"
git branch -M main
git remote add origin https://github.com/<sua-conta>/ebd-boost-vision.git
git push -u origin main
```

### Passo 2 — Conectar Vercel

1. Acesse [vercel.com](https://vercel.com) e faça login com GitHub
2. Clique **Add New → Project**
3. Selecione o repositório `ebd-boost-vision`
4. Em **Framework Preset** escolha `Other` (é estático puro)
5. Em **Build Command** deixe vazio
6. Em **Output Directory** deixe vazio (servirá da raiz)
7. Clique **Deploy**

Em ~30 segundos o Vercel devolve uma URL como `https://ebd-boost-vision-xxxx.vercel.app`. Pronto.

### Atualizar depois

Qualquer `git push` para a branch `main` gera um redeploy automático. Para edição rápida, dá para alterar pelo próprio site do GitHub (botão lápis).

## Domínio próprio (opcional)

No painel do projeto no Vercel → **Settings → Domains** → adicione um domínio (ex: `ebd.sellers.com.br`). O Vercel gera certificado SSL automaticamente.

## Estrutura do repositório

```
ebd-boost-vision/
├── index.html              ← o MVP completo (HTML único)
├── README.md               ← este arquivo
├── vercel.json             ← config do Vercel
├── .gitignore
├── CHANGELOG.md            ← histórico de versões
└── docs/
    ├── COMO_USAR.md        ← guia do usuário final
    └── PLANILHAS.md        ← formato esperado dos CSVs
```

## Importante para o Thomaz / equipe EBD

- **As planilhas continuam manuais.** O Thomaz ou outro analista exporta os 6 CSVs (+ planilha de Produtos opcional + PDF do jornalzinho) e o vendedor faz o upload na tela inicial. Nada é enviado para servidor externo.
- **Dados ficam só no navegador** do vendedor. Cache local guarda geocoding, imagens de produto e progresso de check-in/check-out por vendedor + dia.
- **APIs externas usadas** (gratuitas, todas com CORS aberto):
  - [Nominatim/OpenStreetMap](https://nominatim.openstreetmap.org) — geocoding por endereço (1 req/seg)
  - [OSRM](https://project-osrm.org) — cálculo de rota por carro
  - [ViaCEP](https://viacep.com.br) — fallback de geocoding por CEP
  - [OpenFoodFacts](https://world.openfoodfacts.org) — imagens de produto por EAN

## Limitações conhecidas

- Nominatim trava em ~1 req/seg → 50 clientes ≈ 1 min para geocodificar tudo (cache resolve depois)
- Trânsito ao vivo só aparece quando o vendedor clica **🚦 Trânsito ao vivo** → abre Google Maps nativo
- Imagens de produto dependem do EAN estar cadastrado no OpenFoodFacts; quando não tem, mostra link para Google Imagens
- PDF muito grande (>60 slides) só renderiza canvas das primeiras 30 páginas (texto é lido em todas)

## Suporte

Bugs ou melhorias: abrir issue no GitHub.

---

Versão: v3 · Data: maio/2026 · Construído com React + Leaflet + pdf.js, sem build step.
