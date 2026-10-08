# Explicação dos cálculos

## Entradas
Na aba Simulador: B4 patrimônio inicial; B5 aporte mensal; B6 rentabilidade mensal; B7 taxa de dividendos; B8 prazo em anos; B9 perfil.

## Fórmulas
- Aportes totais (B12): `=B4+B5*B8*12`
- Patrimônio projetado (B13): `=VF(B6;B8*12;-B5;-B4;0)` (armazenada como FV no XLSX).
- Rendimento acumulado (B14): `=B13-B12`
- Dividendos mensais estimados (B15): `=B13*B7`

## Cenários
A aba Cenarios apresenta prazos de 2 a 30 anos e calcula aportes, patrimônio, rendimento e dividendos para cada período.

## PROCV e perfis
A aba Perfis contém distribuições Conservador, Moderado e Arrojado entre Papel, Tijolo, Híbridos e FOFs. Na aba Simulador, B19:B22 utiliza `PROCV($B$9;Perfis!$A$5:$E$7;índice;FALSO)` com índices 2 a 5. A coluna C calcula o valor de cada aporte.

## Intervalos nomeados
A versão inicial utiliza referências absolutas, não nomes definidos. Para cumprir integralmente o requisito, definir no Excel: PatrimonioInicial (Simulador!$B$4), AporteMensal (Simulador!$B$5), TaxaMensal (Simulador!$B$6), PrazoAnos (Simulador!$B$8) e TabelaPerfis (Perfis!$A$5:$E$7), substituindo as referências nas fórmulas.

## Premissas
Capitalização mensal, aportes no fim do mês, rentabilidade constante; sem impostos, taxas ou inflação. Não somar dividendos novamente ao patrimônio para evitar dupla contagem.
