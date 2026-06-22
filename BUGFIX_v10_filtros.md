# v10.2 - Insight refeito (visual) + Agenda como índice (slide 2)

## Insight Rápido — visual novo (por franquia, como pedido)
Antes: um "paredão" de texto numa caixa única.
Agora, em cada slide de Insight (mantidos por grupo de franquia):
- FAIXA "GERAL CONSOLIDADO" no topo: variação grande e colorida (verde/vermelho)
  + 4 chips de métrica (Unidades, Faturamento, Sell-out, Top 5 Clientes).
- CADA FRANQUIA vira um CARTÃO: barra de status colorida, nome + variação no
  cabeçalho, e abaixo Driver / SI×SO / Top produtos. Layout em 2 colunas quando
  há 4+ franquias, 1 coluna quando há menos.
- Emoji 🌍 removido.

## Agenda — agora é o SLIDE 2 (índice das seções)
- Criada logo após a capa (posição 2), em cartões numerados em 2 colunas.
- Lista as 16 seções do relatório.
- Como é criada na ordem certa (não via reorder), os rIds ficam sequenciais
  e o PowerPoint aceita.

## Correções de corrupção (mantidas)
- Caminho dos gráficos absoluto → relativo (causa raiz do "repair")
- addImage bloqueia imagens vazias (0 bytes)
- Sanitização de caracteres XML inválidos
- Marcador "v10.2" no rodapé (confirma que é a versão nova)

## Validação
- Export real com sell-out → 41 slides
- 0 caminhos absolutos, 0 imagens de 0 bytes
- Slide 2 = Agenda; Insights com cartões por franquia
- Render conferido (Agenda e Insight)

## Para usar
1. Substitua o dashboard_template_v10.html
2. RE-RODE o sales_dashboard_v10.py
3. Abra o dashboard novo (Ctrl+Shift+R) e exporte
