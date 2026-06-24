# v10.11 - Correções no Histórico SKU (rodapé: v10.11 sku-fix)

## 1) Franquia errada por SKU — CORRIGIDO
Antes a chave era franquia+produto, então se o sell-out (IQVIA) classificava um
produto numa franquia diferente, criava linha errada (ex.: "Pós-Op + SYSTANE").
Agora a chave é só o PRODUTO normalizado e a FRANQUIA vem do SELL-IN (fonte oficial):
- Sell-in define franquia e nome do produto.
- Target só define franquia se o produto não veio do sell-in.
- Sell-out NUNCA muda a franquia (só soma o valor no produto certo).
Resultado: SYSTANE aparece só em DE&OH; o sell-out dele entra na linha certa.

## 2) Target mês a mês — ADICIONADO
O Excel agora traz colunas de Target mês a mês (TG jan/26 ... dez/26), além do
Target total do ano, Realizado, YTGO e Atingimento. (Antes só tinha o total.)
Estrutura: SO mês a mês (3 anos) · SI mês a mês (3 anos) · TG mês a mês · resumo.

## 3) Card removido (já existe o de Targets Financeiros — Atingimento)
Removi o card "Histórico por SKU" do HTML e o link "Hist. SKU" do menu, pois o
atingimento por produto já está no card "Targets Financeiros — Atingimento" (4º card).
O histórico SKU completo continua disponível pelo botão "Histórico SKU (Excel)"
na barra de exportação (topo).

## Onde exportar
Barra de exportação (topo) → botão "Histórico SKU (Excel)".
