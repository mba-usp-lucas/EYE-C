# v10.2 - Versão com Agenda + todas as correções de corrupção

## O que tem nesta versão
- AGENDA presente (no fim, ordem de criação — ordem estável e segura)
- Marcador "v10.2" no rodapé de cada slide (canto inferior direito)
- Reorder DESATIVADO (estava com bug: punha "Plano de Recuperação" na
  posição errada; e a manipulação interna gerava risco no PowerPoint)
- rIds sequenciais (ordem natural que o PowerPoint aceita)

## As 3 causas de "repair" — todas corrigidas
1. CAMINHO DOS GRÁFICOS absoluto (/ppt/charts/) → relativo (../charts/)
   — confirmado como bug do PptxGenJS 3.12.0 (inclusive no bundle que você usa)
2. IMAGENS DE 0 BYTES (canvas vazio / logo não carregado) → toda addImage
   bloqueia imagem vazia
3. CARACTERES XML inválidos nos dados → sanitizados

## ⚠️ COMO CONFIRMAR QUE É ESTA VERSÃO (decisivo)
Depois de exportar, olhe o RODAPÉ de qualquer slide (canto inferior direito):
deve aparecer "... · v10.2".
- SE VOCÊ VÊ "v10.2": está na versão nova e corrigida.
- SE NÃO VÊ "v10.2": você abriu um arquivo ANTIGO. Refaça:
    1. Substitua o dashboard_template_v10.html
    2. RE-RODE o sales_dashboard_v10.py
    3. Abra o NOVO dashboard_sales_insightsv10.html (Ctrl+Shift+R)
    4. Exporte e abra o .pptx recém-gerado

## Se AINDA der repair MESMO vendo "v10.2"
Então é um caso novo e específico dos seus dados. Ao abrir, o PowerPoint
geralmente mostra o nome de uma PARTE do arquivo (ex.: "/ppt/slides/slide6.xml"
ou "/ppt/charts/chart3.xml"). Me passe esse nome — ele aponta o local exato e
eu corrijo direto, sem suposição.

## Validação (rigorosa, com gráficos reais)
- Export real com sell-out → 41 slides, 6 gráficos
- 0 caminhos absolutos, 0 imagens 0-byte, rIds sequenciais, agenda presente,
  XMLs OK, rels resolvem, python-pptx lê sem erro
