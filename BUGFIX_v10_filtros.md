# v10.9 - Correções na barra de menu (navegação por hiperlinks)

## 1) Link "Targets" não funcionava — CORRIGIDO
O card "Status de Targets" começava com display:none e a função renderTargets só
voltava a escondê-lo (nunca o reexibia). Resultado: o card ficava sempre oculto e
o link do menu não tinha onde rolar. Agora, quando há targets carregados, o card
é exibido (card.style.display=''), e o link passa a funcionar.

## 2) Renomeados itens do menu
- "SI × SO"  → "Comp. SI x SO"  (card Análise Comparativa Sell-in × Sell-out)
- "SI vs SO" → "Evolução SIxSO" (card do gráfico de diferença SI vs SO)

## Observação
Os outros cards condicionais (Comp. SI x SO e Evolução SIxSO) já exibiam
corretamente (display:'block' quando há sell-out) — só o Targets tinha o bug.

## Marcador de versão
Rodapé dos slides agora mostra "v10.9 nav-fix" (para confirmar o build novo).

## Lembrete (sempre que trocar o template)
1. Substituir o dashboard_template_v10.html
2. Rodar de novo o sales_dashboard_v10.py
3. Abrir o HTML e Ctrl+Shift+R (hard refresh)
