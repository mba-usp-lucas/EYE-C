# v10 - Corrupção eliminada (3 causas) + slide vazio tratado

## "Slide 6/7 vem vazio" — esclarecimento
Testei: um slide com painel vazio (sem texto) ou com gráfico não renderizado
NÃO corrompe o arquivo — gera um parágrafo vazio válido. Ou seja, o slide
vazio é um efeito VISUAL, não a causa do "repair".

Os slides 6/7 (na ordem de criação) são "Insight Rápido" ou "Evolução Mensal".
A Evolução Mensal captura um gráfico da tela; se o gráfico não tiver desenhado
ainda (seção fechada / PC lento), o slide vinha vazio. Agora:
- A renderização antes do export ficou mais robusta (força reflow, redesenha
  os gráficos em 2 passadas, espera maior — ~850ms).
- Se mesmo assim o canvas vier vazio, entra um aviso "Gráfico indisponível"
  em vez de uma imagem quebrada (que é o que corrompia antes).

## As 3 causas de "repair" — todas corrigidas
1. CAMINHO DOS GRÁFICOS absoluto (/ppt/charts/) → relativo (../charts/).
2. IMAGENS DE 0 BYTES (canvas vazio OU logo que não carregou): agora TODA
   addImage é interceptada e imagens vazias são ignoradas.
3. CARACTERES XML inválidos nos dados → sanitizados.

## ⚠️ COMO GARANTIR QUE ESTÁ USANDO ESTA VERSÃO (importante!)
Se o erro continuar IDÊNTICO, quase sempre é porque o arquivo testado é o
antigo. Faça nesta ordem:
1. Substitua o dashboard_template_v10.html pelo deste pacote.
2. RE-RODE o sales_dashboard_v10.py (ele lê o template e gera o dashboard).
3. Feche o dashboard antigo. Abra o NOVO dashboard_sales_insightsv10.html.
4. Ctrl+Shift+R (limpa cache).
5. Exporte o PowerPoint (botão PPT).
6. Abra o .pptx recém-gerado (não um exportado antes).

## Validação (rigorosa)
- Export real com sell-out → 41 slides, 6 gráficos
- 0 caminhos absolutos, 0 imagens 0-byte, 0 caracteres de controle,
  rels resolvem, XMLs OK, python-pptx lê sem erro
