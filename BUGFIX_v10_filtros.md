# v10 - HOTFIX: fmtNum is not defined (Systane Unidades)

## 🐛 Erro "fmtNum is not defined" — CORRIGIDO
Na chamada da versão em Unidades do Systane, usei `fmtNum`, mas dentro da
função exportPPTX o formatador de números se chama `fmtNumR` (o `fmtNum`
existe só em outro escopo). Troquei `fmtNum` → `fmtNumR`.

Como o erro era lançado exatamente nessa linha, tudo que vinha antes já
funcionava; era só essa referência.

## ✅ Confirmações de escopo
- fmtNumR: definido dentro do exportPPTX (antes das chamadas Systane) ✅
- fmt, getValor, getValorSO, filtrarBase, selloutCanalOk,
  clienteBateFiltroSO: todos globais/acessíveis ✅
- Nenhum outro fmtNum solto no exportPPTX ✅

## Systane em Reais e Unidades (mantido)
- gerarSlideSystane chamado 2x: métrica selecionada + Unidades
- Versão Unidades pulada se métrica já for UNID

## Recap acumulado
- CORRUPÇÃO (imagens 0 bytes) resolvida
- Systane Reais + Unidades (hotfix aplicado)
- Reorder atômico; Recuperação por último
- Rede→Cliente; Insight limpo; blindagem try/catch
- Top 15 Clientes/Produtos na ordem

## ✅ Validações
- Sintaxe JS OK (4 scripts)
- python-pptx (estrito): exemplo íntegro
