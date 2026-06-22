# v10.6 - Correção dos insights em branco + SI vs PY visível

## Insights em branco — CORRIGIDO
Causa: no bloco de "Ações" (novo), se algum item do plano de ação vinha nulo,
o acesso a item.franquia lançava exceção e o slide de insight inteiro ficava
em branco (só o banner). Correções:
- Guardas a && Array.isArray() no bloco de Ações
- try/catch no cálculo do GERAL, na análise por franquia e nas Ações
  → se qualquer parte falhar, o insight ainda renderiza (nunca fica em branco)

## "SI vs PY" agora bem visível nos insights
Aparece em 3 lugares em cada slide de insight:
- Faixa GERAL: "Impacto: Sell-in (SI) vs PY" (azul, negrito)
- Cabeçalho de cada cartão de franquia: "... · SI vs PY"
- Rodapé: "impacto em Sell-in (SI) vs ano anterior (PY)"

## Mantido
- Insight por franquia com detalhe completo (Driver, SI×SO, Top produtos,
  Movers, Top clientes, Ações/Foco) · grupos 1=DE&OH+CLC, 2=Glaucoma+Patanol, 3=CL
- V×P×Mix fora da recuperação · Top 15 com Atual SI/SO e Δ% PY ·
  Detalhamento SI×SO · Systane Unidades→Reais · sem slides-fantasma

## Validação
- 45 slides · 0 absolutos · 0 imagens 0-byte · nenhum sem banner
- Todos os insights com conteúdo (não-brancos) · SI vs PY em 3 pontos
