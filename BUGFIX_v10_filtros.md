# v10 - Systane em UNIDADES + esclarecimento slide 2

## ✅ Systane últimos 12 meses — agora em REAIS e UNIDADES
O bloco da Tendência por Systane virou uma função reutilizável
(gerarSlideSystane) chamada duas vezes:
1. Métrica selecionada (ex.: Reais) — título "Tendência por Systane · Reais"
2. Unidades — título "Tendência por Systane · Unidades"
(a 2ª é pulada se a métrica já for Unidades, para não duplicar.)

Cada versão mantém: sell-in + sell-out por produto, card Família,
agrupamento Complete, e a correção de tamanho de série (anti-corrupção).
Os dois slides ficam adjacentes na ordem (ambos rank 11).

## ℹ️ Slide 2 "fora de contexto" — esclarecimento
Com a reordenação funcionando corretamente (agora que a corrupção foi
resolvida), a sequência real é:
  1. Capa
  2. Agenda
  3. Indicadores & Benchmark
  4. Análise por Tipo de Cliente
  ...
A posição 2 é a AGENDA (correto). O slide "fora de contexto" que aparecia
antes vinha do arquivo corrompido/antigo, onde a reordenação não era aplicada.
Ao reexportar com o HTML corrigido, a posição 2 deve ser a Agenda.

Se, mesmo assim, houver um slide deslocado, me envie o TÍTULO EXATO dele
(o que está escrito no topo) que eu ajusto o reposicionamento.

## Recap acumulado
- CORRUPÇÃO resolvida (imagens de 0 bytes → helper addCanvasImg)
- Systane: Reais + Unidades
- Reorder atômico; Plano de Recuperação por último
- Rede→Cliente; Insight sem bullets vazios; blindagem try/catch
- Top 15 Clientes e Produtos (Rede/Distribuidor) na ordem

## ✅ Validações
- Sintaxe JS OK (4 scripts)
- python-pptx (estrito): arquivos íntegros
- Reorder: posição 2 = Agenda, Systane Reais/Unidades adjacentes
