# v10.3 - 6 ajustes solicitados

1. SYSTANE: agora gera Tendência em UNIDADES e, em sequência, em REAIS (sell-in).
2. TARGETS FINANCEIROS (slide do "card gigante"): o espaço vazio abaixo dos 3
   cards agora traz a tabela DE&OH (atingimento por produto: Real/Tgt/Atg de
   Mês e YTD). O slide de detalhe por franquia continua existindo.
3. SLIDES SEM BANNER/TÍTULO: eram slides-fantasma criados pelo autoPage do
   PptxGenJS quando uma tabela passava do fim da página. Agora TODAS as tabelas
   têm autoPage:false → nenhum slide extra sem cabeçalho.
4. TOP 15 QUEDAS/CRESCIMENTOS: coluna "Δ Abs" renomeada para "Δ Abs PY".
5. SLIDE 17 (Top 15 Crescimentos): colunas "Atual"→"Atual SI" e "Δ %"→"Δ % PY".
   Coluna "#" alargada (não quebra mais com números de 2 dígitos).
6. SLIDE 4 (Tipo de Cliente): tabela com altura/fonte adaptativas ao nº de
   tipos — com muitos tipos (ex.: 12) a tabela compacta e cabe na tela.

## Correções de corrupção (mantidas)
- Caminho dos gráficos relativo · addImage bloqueia imagem vazia ·
  sanitização XML · autoPage:false (também evita corrupção por tabela órfã)
- Marcador "v10.2/3" no rodapé

## Validação (com dados de target + sell-out)
- 44 slides · 0 caminhos absolutos · 0 imagens 0-byte · nenhum slide sem banner
- "Atual SI" e "Δ Abs PY" confirmados · Systane Unidades→Reais · DE&OH no sTgt
