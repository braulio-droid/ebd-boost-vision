# Changelog — EBD Boost Vision

## v3.0 — maio/2026

Primeira versão deployada (MVP de campo).

### Briefing como main screen
- Layout 3 colunas: Sequência da rota + Carteira (col 1) · Mapa (col 2) · Detalhes do cliente (col 3)
- Drag-and-drop nativo HTML5 para incluir, reordenar e remover clientes
- Painel "Rota do dia" com progresso, ETA, tempo médio
- Botão "🚦 Trânsito ao vivo" abre Google Maps com rota completa

### Copiloto de visitas
- Check-in / Check-out por cliente persistido em localStorage (por vendedor + dia)
- Pinos do mapa mudam de cor por status (em visita = azul pulsante, concluído = ✓ cinza)
- Após check-out, abre automaticamente o Google Maps com rota para o próximo cliente
- URL com `dir_action=navigate` que entra direto em modo navegação no celular

### Inteligência cruzada
- Recomendação de produto em 4 categorias: Reposição (já compra + informativo), Novo do informativo (cliente similar do mesmo ramo), Recompra esquecida, Campanha aplicável
- Alertas estratégicos no topo: clientes 90+ na rota, cesta × informativo, campanhas aplicáveis
- Detecção automática de promoções no PDF (EAN + SKU + desconto)

### Cliente 360 com abas
- Aba Sugestões (com sub-filtros por tipo)
- Aba Perfil (hierarquia comercial completa)
- Aba Histórico (timeline com fotos)
- Foto do produto via OpenFoodFacts (gratuito, por EAN)

### Mapa interativo
- Leaflet + OpenStreetMap (gratuito)
- Geocoding via Nominatim com 4 estratégias de fallback
- Fallback final via ViaCEP para casos sem match
- Roteamento via OSRM (driving)
- Otimização por Nearest Neighbor opcional

### Outras abas
- **Visão Geral**: KPIs consolidados, classificação 30/90+, transparência de fontes
- **Recuperação 90+**: lista filtrável de críticos sem compra
- **Informativo**: grid visual de produtos com busca por nome, marca, fabricante, categoria
- **Campanhas**: detecção automática dos últimos slides do PDF + validação dupla
- **Resumo Vendedor**: PI pessoal — top ramos, top produtos, positivação
- **Painel Supervisor**: ranking por risco de carteira
- **Qualidade**: diagnóstico de relacionamentos entre bases

### Persistência local
- `ebd_geo_v3` — cache de geocoding
- `ebd_imgs_v3` — cache de imagens OpenFoodFacts
- `ebd_visitas_v3` — check-in/out por vendedor + dia

### Decisões técnicas registradas
- 90 dias para clientes críticos (não 60) — decisão Thomaz
- Estoque alto = Days on Hand alto (não quantidade absoluta)
- "Rota inteligente" geral foi descartada (gestão é do supervisor) — só rota para recuperação
- Sem chat IA: vendedor low-tech, tudo via clique
- Sem backend: planilhas continuam manuais
