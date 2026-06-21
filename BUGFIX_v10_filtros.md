# v10 - CORREÇÃO DEFINITIVA da corrupção (validada rodando o export real)

## 🎯 CAUSA RAIZ FINAL: caracteres XML inválidos nos dados
Dados de IQVIA/SAP frequentemente contêm caracteres de controle invisíveis
(\x00, \x07, \x1F, etc.) e Unicode inválido dentro de nomes de produto,
cliente ou franquia. O PptxGenJS NÃO remove esses caracteres, e o PowerPoint
recusa qualquer XML que os contenha (erro "repair / não consegue ler").
O LibreOffice tolerava, por isso não aparecia nos testes anteriores.

## ✅ Correção (100% — validada executando o export de verdade)
Interceptamos addText, addTable e addChart de TODOS os slides para remover
caracteres XML inválidos de qualquer texto antes de gravar. Aplicado nos
dois exports (principal e One-Pager).

Como foi validado:
- Rodei o exportPPTX REAL (PptxGenJS de verdade, não teste isolado)
- Injetei dados com \x1F, \x07, \x00 em nomes (como dados SAP reais)
- Forcei canvas vazios (a outra causa, já corrigida)
- Resultado: 36 slides, 0 caracteres de controle, 0 imagens de 0 bytes,
  arquivo lido pelo python-pptx (rígido como o PowerPoint) SEM erro

## Resumo das DUAS causas de corrupção (ambas corrigidas)
1. Imagens de 0 bytes (canvas não renderizado) → helper addCanvasImg
2. Caracteres XML inválidos nos dados → sanitização em addText/Table/Chart

## Demais entregas (mantidas)
- Systane em Reais e Unidades (Tendência por Systane · Unidades)
- Reorder atômico; Plano de Recuperação por último
- Rede→Cliente; Insight sem bullets vazios; Top 15 na ordem
- fmtNum → fmtNumR corrigido

## ✅ Validações
- Sintaxe JS OK (4 scripts)
- Export REAL executado com dados problemáticos: arquivo íntegro
- python-pptx (estrito): lê sem erro, sem caracteres inválidos
