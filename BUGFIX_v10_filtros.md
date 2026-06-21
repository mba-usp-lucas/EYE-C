# v10 - Correções: Rede→Cliente, Insight, blindagem, ordem

## ✅ Slide 9 "REDE" → "CLIENTE"
Na Análise Comparativa (níveis Produto/Cliente/Franquia), "Rede" virou
"Cliente". Emoji 🔬 removido. Título "Resumo Comparativo" agora é
"Resumo Comparativo · Key Accounts".

## ✅ Insight Rápido — bullets vazios removidos
Agora filtra automaticamente bullets sem conteúdo (ex.: "Driver: " sem valor,
": n/d", linhas vazias) e remove emojis decorativos. Fica mais visual e
menos poluído.

## ✅ Slides 6/7/8 que "não apareciam" — CAUSA E CORREÇÃO
Causa provável: um bloco novo (slide Acima/Abaixo do Target ou sell-out do
Systane) dava ERRO no seu ambiente real, abortando o export inteiro — então
você via um arquivo antigo, sem os slides novos.
Correção: blindei essas adições com try/catch. Agora, se algo falhar num
slide específico, ele degrada sozinho e o restante do PPT é gerado normalmente.

## ✅ Ordem dos slides — Top 15 incluídos
A reordenação agora posiciona explicitamente:
- Top 15 Clientes
- Top 15 Produtos · Canal Rede e Canal Distribuidor
- Sell-in × Sell-out · Diferença · Unidades (12m)
Todos entram na sequência (não vão mais para o final). Testado: nenhum
slide é perdido.

## ⏳ PENDENTE (próxima rodada)
- Systane últimos 12 meses em UNIDADES (versão separada, além de Reais)
- Slide 2 "fora de contexto" → preciso que você confirme, no novo export,
  QUAL slide está na posição 2 (título), pois com a reordenação a pos. 2
  agora é a Agenda. Se ainda houver um slide deslocado, me diz o título.
- Slide 7 (Evolução Mensal) sell-in: depende do gráfico chartYoY renderizar;
  a correção de expandir seções antes do export deve resolver — confirmar.

## ✅ Validações
- Sintaxe JS OK (4 scripts)
- Reorder testado: 30→30 slides, Top 15 nas posições certas
