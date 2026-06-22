# v10.7 - Insights em branco DEFINITIVAMENTE corrigidos

## Causa raiz do branco
A renderização dos detalhes do cartão usava runs de texto com bullet + breakLine
(array de objetos). Esse caminho funciona no validador, mas o bundle do PptxGenJS
do PC corporativo reage diferente e lançava exceção → o slide de insight inteiro
ficava em branco.

## Correção
- Detalhes do cartão agora usam STRING SIMPLES (com "• " no começo de cada linha),
  igual à versão de insight que você aprovou. Sem runs com bullet/breakLine.
- Cabeçalho do cartão também virou string simples.
- Toda a renderização do insight está em try/catch: se algo falhar, cai num
  fallback de texto puro → o insight NUNCA fica em branco.
- Mantidas as guardas (a && Array.isArray) no bloco de Ações.

## SI vs PY bem visível (em 3 lugares por slide)
- Faixa GERAL: "Impacto: Sell-in (SI) vs PY" (azul, negrito)
- Cabeçalho de cada cartão: "... · SI vs PY"
- Rodapé: "impacto em Sell-in (SI) vs ano anterior (PY)"

## Testado com SUAS franquias reais
Reproduzi com DE&OH, CLC, Glaucoma, Pós-Op & Patanol S, CL (grupos 2/2/1):
todos os 3 insights renderizam com conteúdo completo (Driver, SI×SO, Top produtos,
Movers, Top clientes) e SI vs PY visível.

## Validação
- 45 slides · 0 absolutos · 0 imagens 0-byte · nenhum sem banner · insights com conteúdo
