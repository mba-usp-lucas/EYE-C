# v10 - CORREÇÃO CRÍTICA: arquivo corrompido (PowerPoint "repair")

## 🐛 Erro "repair / não consegue ler" — CORRIGIDO
Causa: no slide de Tendência por Systane, os arrays de dados tinham SEMPRE
12 posições (Array(12)), mas os rótulos de mês (labels) podiam ter MENOS de
12 quando havia menos de 12 meses de dados. Essa diferença de tamanho entre
values e labels gera um gráfico inválido que o PowerPoint recusa (pede reparo),
mesmo o LibreOffice abrindo.

Correção:
- Os valores dos gráficos Systane (sell-in e sell-out) agora são alinhados
  ao número de rótulos (values.slice(0, labels.length)).
- Valores não-numéricos (NaN/Infinity) são trocados por 0 (sanitização).

## 🛡️ Reordenação agora é ATÔMICA e segura
A reorganização da ordem só é aplicada se preservar exatamente os mesmos
slides (mesma quantidade, sem duplicatas, todos presentes). Se algo não bater,
mantém a ordem original — nunca corrompe nem perde slides.

## ✅ Plano de Recuperação por ÚLTIMO
Movido para o fim de tudo (depois inclusive dos slides não listados como Mix
por Franquia).

## ✅ Slides Sell-in × Sell-out em sequência
Os pares relacionados (Evolução Mensal SI/SO, Diferença 12m valor/unidades)
ficam adjacentes na ordem.

## Recap das correções desta rodada + anteriores
- CRÍTICO: corrupção do PPT (Systane) corrigida
- Reorder atômico (à prova de perda de slides)
- Plano de Recuperação por último
- Slide 9 "Rede" → "Cliente"; Resumo → "Key Accounts"
- Insight Rápido: bullets vazios removidos
- Blindagem (try/catch) nos slides novos
- Top 15 Clientes e Produtos (Rede/Distribuidor) na ordem

## ⏳ PENDENTE
- Systane últimos 12 meses em UNIDADES (versão separada, além de Reais)
- Confirmar qual slide estava na posição 2 fora de contexto

## ✅ Validações
- Sintaxe JS OK (4 scripts)
- Gráfico com labels<12: agora gera arquivo íntegro (testado)
- Reorder atômico testado (sem perda)
