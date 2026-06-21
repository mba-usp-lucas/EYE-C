# v10 - CORREÇÃO DEFINITIVA: caminho dos gráficos (causa raiz do "repair")

## 🎯 CAUSA RAIZ REAL (confirmada no código do PptxGenJS)
O PptxGenJS gera o caminho (Target) dos GRÁFICOS como ABSOLUTO:
    Target="/ppt/charts/chart1.xml"
enquanto imagens usam caminho RELATIVO (../media/...). O PowerPoint RECUSA
caminhos absolutos em relationships e pede reparo ("repair / não consegue ler").
O python-pptx e o LibreOffice toleram — por isso só o PowerPoint acusava.

Como todo slide com gráfico nativo (Systane, Diferença SI×SO, Movers) tinha
esse caminho absoluto, qualquer um desses bastava para corromper o arquivo.

## ✅ Correção
Antes de salvar, percorremos todos os slides e trocamos o caminho dos
gráficos de "/ppt/charts/..." para "../charts/..." (relativo). Aplicado nos
dois exports (principal e One-Pager).

## ✅ Como foi validado (rigoroso)
- Inspeção do código-fonte do PptxGenJS: confirmado Target absoluto (linha 1910)
- Export REAL executado com sell-out → gráficos Systane de 2 séries
- Resultado: 6 gráficos, TODOS com caminho relativo, 0 caminhos absolutos
- Validação exaustiva do pacote: XMLs bem-formados, todos os rels resolvem,
  content-types completo, python-pptx lê sem erro

## ✅ Recursos reativados (não eram a causa)
- Systane em Unidades (Tendência por Systane · Unidades)

## Estado atual
- Reordenação: DESATIVADA (mantém ordem de criação, rIds sequenciais)
- Systane: Reais + Unidades
- Proteções: sanitização XML + bloqueio de imagens 0 bytes + caminho relativo

## Resumo de TODAS as causas de "repair" encontradas e corrigidas
1. Imagens de 0 bytes (canvas vazio) → helper addCanvasImg
2. Caracteres XML inválidos nos dados → sanitização addText/Table/Chart
3. Caminho ABSOLUTO dos gráficos → conversão para relativo  ← a definitiva

## ✅ Validações
- Sintaxe JS OK (4 scripts)
- Export real com gráficos: pacote 100% válido, caminhos relativos
