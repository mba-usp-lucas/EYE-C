# v10 - VERSÃO ESTÁVEL (reordenação desativada)

## ✅ O que foi feito
A reordenação automática dos slides (que reorganizava na "ordem executiva")
foi DESATIVADA. Ela manipulava o array interno de slides do PptxGenJS, o que
deixava as referências internas (rIds) fora de ordem sequencial. Apesar de
ser tecnicamente válido (e o python-pptx/LibreOffice aceitarem), o PowerPoint
recusava o arquivo ("repair").

Agora os slides saem na ORDEM DE CRIAÇÃO (rIds sequenciais), que é o
comportamento estável — como na versão que abria sem erro.

## ✅ Proteções mantidas (não atrapalham, só ajudam)
- Sanitização de caracteres XML inválidos (controle \x00/\x07/\x1F etc.)
- Bloqueio de imagens de 0 bytes (canvas não renderizado)

## ✅ Conteúdo mantido (são operações padrão e seguras)
- Systane em Reais e Unidades
- Slide Produtos Acima/Abaixo do Target
- Faixas/ícones, Rede→Cliente, Insight limpo, Targets %PY, etc.

## Ordem atual dos slides (criação)
Capa · Indicadores · Tipo de Cliente · Resumo (Key Accounts) ·
Comparativa SI×SO · Insight · Plano de Ação · Evolução Mensal (SI e SO) ·
Status Targets FOCO · Mix Franquia · Franquia comparativo ·
Top 15 Clientes · Top 15 Produtos (Rede) · Top 15 Produtos (Distribuidor) ·
Top 15 Crescimentos · Diagnóstico Crescimento · Top 15 Quedas ·
Diagnóstico Queda · Systane (Reais) · Systane (Unidades) ·
Diferença 12m (valor) · Diferença 12m (unidades) · Movers ·
Targets Financeiros · Detalhe por Franquia · Acima/Abaixo Target ·
Crescimento por Produto (SI e SO) · Plano de Recuperação · Agenda

OBS: a Agenda fica por último (era reposicionada pela reordenação).
Se quiser a "ordem executiva" de volta, dá para fazer de forma segura
reordenando a SEQUÊNCIA DE CRIAÇÃO no código (sem mexer no array interno) —
mas só depois de confirmar que este arquivo abre normal no PowerPoint.

## ✅ Validação
- Export REAL executado com dados problemáticos: arquivo íntegro
- rIds sequenciais (ordem natural que o PowerPoint aceita)
- python-pptx: lê sem erro
