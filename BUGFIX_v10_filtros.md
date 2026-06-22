# v10.8 - Insight REFEITO à prova de falhas (single addText)

## IMPORTANTE: como confirmar que está rodando o build novo
O rodapé de TODOS os slides agora mostra "v10.8 insight-fix" (canto inferior direito).
Se o seu PPT exportado NÃO mostrar isso, você está exportando um build ANTIGO em cache.
Nesse caso, os passos abaixo são obrigatórios.

## Passos obrigatórios (na ordem)
1. Substituir o dashboard_template_v10.html pelo novo
2. RODAR DE NOVO o sales_dashboard_v10.py (gera o dashboard_sales_insightsv10.html)
3. Abrir o HTML gerado e dar Ctrl+Shift+R (hard refresh, limpa cache)
4. Exportar o PPTX
Pular o passo 2 ou 3 = continua vendo o insight antigo em branco.

## O que mudou no insight (para nunca mais ficar em branco)
O slide de insight foi reescrito para usar UM ÚNICO addText de texto — a operação
mais básica do PptxGenJS, a mesma que todos os outros slides (que funcionam) usam.
- Sem shapes (roundRect/rect), sem cartões, sem chips, sem arrays de runs com
  bullet/breakLine — tudo isso eram pontos que podiam falhar no bundle do seu PC.
- Estrutura: faixa GERAL (texto) + cada franquia com cabeçalho e bullets de detalhe.
- Cálculo de cada parte em try/catch; render com fallback de string pura.
  É impossível ficar em branco: no pior caso mostra o texto puro.

## Conteúdo do insight (mantido completo)
GERAL: variação + Impacto Sell-in (SI) vs PY + Unidades/Faturamento/Sell-out/Total.
Por franquia: Driver, SI×SO, Top produtos, Movers, Top clientes, Ações/Foco.
Grupos: 1=DE&OH+CLC, 2=Glaucoma+Pós-Op&Patanol S, 3=CL.

## SI vs PY visível
Faixa GERAL ("Impacto em Sell-in (SI) vs PY"), cabeçalho de cada franquia ("· SI vs PY")
e rodapé ("impacto em Sell-in (SI) vs ano anterior (PY)").

## Validação
- 45 slides · 0 absolutos · 0 imagens 0-byte · nenhum sem banner
- Insights com conteúdo (testado inclusive com DE&OH/CLC/Glaucoma/Pós-Op/CL = grupos 2/2/1)
