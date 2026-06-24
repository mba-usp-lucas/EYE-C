# v10.10 - Hiperlinks robustos + Histórico SKU VISÍVEL no HTML

## CONFIRA O BUILD: rodapé dos slides mostra "v10.10 hist-sku"
Se não mostrar, você está num build antigo (cache). Refaça: trocar HTML →
rodar sales_dashboard_v10.py → abrir HTML → Ctrl+Shift+R.

## 1) Hiperlinks do menu — agora robustos
A função scrollToSection foi reforçada:
- Se o card de destino estiver oculto (display:none), ele é exibido antes de rolar.
- Fallback para navegadores corporativos antigos (sem rolagem suave): usa
  window.scrollTo(0,y) e, em último caso, scrollIntoView.
- Pequeno atraso para o layout assentar antes de rolar.
Com isso todos os links do menu passam a funcionar, inclusive Targets e o novo Hist. SKU.

## 2) Histórico por SKU agora aparece NO HTML (não era só export)
Novo card "Histórico por SKU · Sell-in × Sell-out × Target" (entre Targets e Evolução),
com link "Hist. SKU" no menu. Mostra uma tabela por SKU:
- Franquia, Produto
- Sell-out 2026, Sell-in 2026 (ano corrente)
- Target 2026, YTGO (Target − Sell-in), Atingimento % (com cores)
O botão verde "Excel (mês a mês, 3 anos)" no cabeçalho do card exporta o histórico
mensal completo (sell-out e sell-in dos últimos 3 anos) — a tabelona.
O sell-out casa com sell-in/target pelo nome normalizado (ignora sufixos tipo "(NVR)").

## Observação
A tabela no HTML é o RESUMO do ano (cabe na tela). O detalhe mês a mês de 3 anos
fica no Excel (são 70+ colunas, inviável na tela).
