# COMO CRIEI A FERRAMENTA DE SIMULAÇÃO DE INVESTIMENTOS

**Projeto:** R Tulio Investimentos  
**Ferramenta utilizada:** Microsoft Excel  
**Objetivo:** simular aportes mensais, patrimônio acumulado, dividendos e distribuição do investimento conforme o perfil do investidor.

> Esta ferramenta possui finalidade educacional e de planejamento. Os resultados são estimativas e não representam garantia de rentabilidade ou recomendação individual de investimento.

---

## 1. OBJETIVO DO PROJETO

Criei esta ferramenta para transformar informações financeiras simples em uma simulação de investimentos fácil de compreender.

O usuário informa:

- salário mensal;
- valor que pretende investir por mês;
- prazo do investimento;
- taxa mensal estimada de juros;
- taxa mensal estimada de dividendos;
- perfil do investidor.

A ferramenta calcula automaticamente:

- sugestão de investimento com base no salário;
- patrimônio acumulado;
- dividendos mensais estimados;
- resultados para diferentes prazos;
- distribuição do aporte conforme o perfil;
- representação gráfica da distribuição.

---

## 2. ESTRUTURA DA PLANILHA

A pasta de trabalho possui duas abas principais.

### Aba INVESTIMENTOS

É a tela principal utilizada pelo usuário. Ela contém:

1. configurações financeiras;
2. simulação do investimento mensal;
3. comparação entre diferentes prazos;
4. escolha do perfil do investidor;
5. distribuição do aporte;
6. gráfico da alocação.

### Aba PERFIS

É uma tabela auxiliar que armazena os percentuais utilizados para cada perfil.

| Perfil | Tijolo | Papel | Infraestrutura / Novos Setores |
|---|---:|---:|---:|
| Conservador | 55% | 40% | 5% |
| Moderado | 45% | 35% | 20% |
| Agressivo | 30% | 30% | 40% |

Todos os perfis somam 100%.

---

## 3. CONFIGURAÇÕES FINANCEIRAS

As principais informações utilizadas pela ferramenta são:

| Informação | Exemplo |
|---|---:|
| Salário mensal | R$ 3.000,00 |
| Taxa mensal estimada de dividendos | 0,75% |
| Investimento mensal | R$ 450,00 |
| Prazo | 5 anos |
| Taxa mensal estimada de juros | 1,04% |
| Perfil escolhido | Conservador |

Os campos editáveis foram destacados visualmente para facilitar a utilização.

---

## 4. SUGESTÃO DE INVESTIMENTO

Utilizei a seguinte fórmula:

```excel
=D11*30%
Essa fórmula calcula 30% do salário informado.

Com um salário de R$ 3.000,00, a sugestão será:

R$ 3.000,00 × 30% = R$ 900,00
Escolhi essa fórmula porque ela permite que a sugestão seja atualizada automaticamente sempre que o salário for alterado.

O percentual de 30% é apenas uma referência educacional. O usuário pode definir outro valor de aporte no campo “Quanto investir por mês?”.

5. CÁLCULO DO PATRIMÔNIO ACUMULADO
Para calcular o patrimônio acumulado, utilizei a função de valor futuro:

=VF(D18;D17*12;-D16)
A fórmula considera:

D18: taxa de juros mensal;
D17*12: prazo convertido de anos para meses;
D16: investimento mensal;
sinal negativo no aporte: representa uma saída financeira do usuário.
Por que utilizei a função FV?
A função FV considera os juros compostos.

Somar somente os aportes mostraria apenas o dinheiro investido, sem considerar o rendimento acumulado ao longo do tempo.

Também foi necessário multiplicar os anos por 12 porque:

o aporte é mensal;
a taxa é mensal;
portanto, os períodos também devem ser mensais.
Exemplo
Considerando:

aporte mensal de R$ 450,00;
prazo de 5 anos;
taxa de 1,04% ao mês;
o patrimônio projetado é:

R$ 37.227,72
A simulação considera aportes no final de cada mês.

6. CÁLCULO DOS DIVIDENDOS MENSAIS
Utilizei a seguinte fórmula:

=D19*$D$12
Ela multiplica o patrimônio acumulado pela taxa mensal estimada de dividendos.

Considerando:

patrimônio de R$ 37.227,72;
dividendos estimados de 0,75% ao mês;
o resultado será:

R$ 279,21 por mês
Utilizei uma referência absoluta em $D$12 para que a taxa permaneça fixa quando a fórmula for copiada.

Os dividendos reais podem variar conforme resultados dos fundos, vacância, inadimplência, mercado e decisões dos gestores.

7. SIMULAÇÃO DE DIFERENTES PRAZOS
Criei cenários para:

2 anos;
5 anos;
10 anos;
20 anos;
30 anos.
A fórmula utilizada foi:

=FV($D$18,$A23*12,-$D$16)
A coluna A contém o número de anos de cada cenário.

As referências do aporte e da taxa foram fixadas porque devem ser as mesmas em todas as linhas.

Resultados do exemplo atual
Prazo	Patrimônio projetado	Dividendos mensais
2 anos	R$ 12.195,80	R$ 91,47
5 anos	R$ 37.227,72	R$ 279,21
10 anos	R$ 106.485,20	R$ 798,64
20 anos	R$ 475.029,55	R$ 3.562,72
30 anos	R$ 1.750.558,33	R$ 13.129,19
Criei esses cenários para demonstrar visualmente como o tempo e os juros compostos influenciam o patrimônio.

8. DIVIDENDOS DOS CENÁRIOS
Para calcular os dividendos de cada cenário, utilizei:

=C23*$D$12
A fórmula multiplica o patrimônio projetado de cada prazo pela taxa mensal estimada de dividendos.

Separei patrimônio e dividendos porque representam informações diferentes:

patrimônio é o valor acumulado;
dividendos representam uma estimativa de renda mensal.
9. ESCOLHA DO PERFIL DO INVESTIDOR
Criei uma lista suspensa com três opções:

Conservador;
Moderado;
Agressivo.
A lista suspensa reduz erros de digitação e garante que a escolha corresponda aos perfis registrados na aba PERFIS.

Ao trocar o perfil, os percentuais, os valores e o gráfico são atualizados automaticamente.

Perfil Conservador
Categoria	Percentual
Tijolo	55%
Papel	40%
Infraestrutura / Novos Setores	5%
Este perfil prioriza uma distribuição com menor participação em setores considerados mais específicos ou sujeitos a maior incerteza.

Perfil Moderado
Categoria	Percentual
Tijolo	45%
Papel	35%
Infraestrutura / Novos Setores	20%
Este perfil procura equilibrar geração de renda, diversificação e exposição a novos setores.

Perfil Agressivo
Categoria	Percentual
Tijolo	30%
Papel	30%
Infraestrutura / Novos Setores	40%
Este perfil aceita maior exposição a categorias com mais incerteza e potencial de oscilação.

Esses percentuais são referências educacionais. O perfil real depende dos objetivos, prazo, liquidez, conhecimento e tolerância a perdas do investidor.

10. BUSCA AUTOMÁTICA DOS PERCENTUAIS
Utilizei a seguinte fórmula:

=SEERRO(SOMASES(PERFIS!$D$3:$D$11;PERFIS!$B$3:$B$11;$D$29;PERFIS!$C$3:$C$11;B33);"")
A fórmula procura na aba PERFIS um percentual que atenda a dois critérios:

perfil selecionado;
tipo de fundo da linha.
Por que utilizei SUMIFS?
A função permite localizar o percentual usando mais de um critério.

Isso torna a ferramenta flexível e permite alterar ou incluir novos perfis sem precisar reconstruir toda a planilha.

Por que utilizei IFERROR?
O IFERROR evita que o usuário veja erros caso algum perfil ou categoria não seja encontrado.

Nesse caso, a célula permanece vazia.

11. CÁLCULO DO VALOR POR CATEGORIA
Utilizei a fórmula:

=IF(C33="","",C33*$D$30)
Essa fórmula multiplica:

percentual sugerido;
investimento mensal.
Se o percentual estiver vazio; o resultado também fica vazio.### Exemplo para o perfil Conservador

Considerando um aporte mensal de R$ 450;0:

Categoria	Percentual	Valor
Tijolo	55%	R$ 247;50
Papel	40%	R$ 180;0
Infraestrutura / Novos Setores	5%	R$ 22;50
Total	100%	R$ 450;0
12 CONFERÊNCIA DOS TOTAIS
Para conferir os percentuais; utilizei:

=SOMA(C33:C35)```

Para conferir os valores, utilizei:

```excel
=SOMA(D33:D35)
Essas fórmulas verificam se:

os percentuais totalizam 100%;
os valores distribuídos correspondem ao aporte mensal.
Essa validação é importante para evitar que parte do dinheiro fique sem distribuição ou que os percentuais ultrapassem 100%.

13. UTILIZAÇÃO DO GRÁFICO
Criei um gráfico de pizza chamado:

Alocação por Tipo de FII
O gráfico apresenta a distribuição entre:

Tijolo;
Papel;
Infraestrutura / Novos Setores.
Por que utilizei um gráfico?
O gráfico ajuda o usuário a:

entender a distribuição sem analisar apenas números;
comparar rapidamente as categorias;
perceber concentrações excessivas;
visualizar as mudanças ao selecionar outro perfil;
tomar decisões com mais clareza.
Ele funciona como uma referência visual e é atualizado automaticamente quando o perfil é alterado.

14. PADRONIZAÇÃO DAS CORES
Utilizei as seguintes cores:

Categoria	Cor
Tijolo	Dourado
Papel	Azul
Infraestrutura / Novos Setores	Verde
As mesmas cores foram aplicadas na tabela e no gráfico.

Essa padronização facilita a associação entre cada linha e a respectiva fatia do gráfico.

15. IDENTIDADE VISUAL
A planilha foi configurada com:

fonte Aptos;
cabeçalhos em azul-marinho;
detalhes em dourado;
campos de entrada em amarelo suave;
resultados em verde suave;
bordas discretas;
valores monetários formatados em reais;
percentuais formatados corretamente;
ausência de linhas de grade;
banner “R TULIO INVESTIMENTOS”.
Justificativa das escolhas
Amarelo: identifica os campos que podem ser alterados;
Verde: identifica resultados calculados;
Azul-marinho: transmite organização e profissionalismo;
Dourado: reforça a identidade relacionada a investimentos;
Bordas: separam os blocos sem deixar a tela carregada;
Banner como imagem: evita deformações ao alterar linhas e colunas.
16. EXEMPLO COMPLETO
Premissas:

salário: R$ 3.000,00;
aporte mensal: R$ 450,00;
prazo: 5 anos;
juros: 1,04% ao mês;
dividendos: 0,75% ao mês;
perfil: Conservador.
Resultados:

sugestão de investimento: R$ 900,00;
patrimônio projetado: R$ 37.227,72;
dividendos mensais estimados: R$ 279,21;
Tijolo: R$ 247,50;
Papel: R$ 180,00;
Infraestrutura / Novos Setores: R$ 22,50;
total distribuído: R$ 450,00.
17. TESTES REALIZADOS
Foram conferidos:

conversão dos anos em meses;
utilização correta da função FV;
atualização do patrimônio;
atualização dos dividendos;
atualização dos cenários;
troca automática dos percentuais por perfil;
soma dos percentuais em 100%;
soma dos valores igual ao aporte;
eliminação dos erros #N/D;
atualização automática do gráfico.
18. LIMITAÇÕES
A ferramenta não considera automaticamente:

inflação;
impostos;
taxas de administração;
corretagem;
oscilação do preço das cotas;
variação dos dividendos;
vacância;
inadimplência;
risco de crédito;
aportes extraordinários;
aumento anual do aporte;
alterações na carteira;
reinvestimento parcial dos dividendos.
A categoria “Infraestrutura / Novos Setores” foi agrupada para simplificar a ferramenta.

Em uma versão futura, seria adequado separar FI-Infra de fundos imobiliários, pois eles podem possuir estruturas e riscos diferentes.

19. MELHORIAS FUTURAS
A ferramenta poderá receber:

separação entre Infraestrutura e Novos Setores;
cálculo com inflação;
valores reais e nominais;
aporte inicial;
aumento anual dos aportes;
cenários pessimista, base e otimista;
rentabilidade anual equivalente;
comparação entre valor projetado e realizado;
proteção das células de fórmula;
alertas quando os percentuais não somarem 100%;
página de instruções;
histórico mensal dos investimentos.
20. CONCLUSÃO
A ferramenta combina:

matemática financeira;
juros compostos;
fórmulas automáticas;
validação de dados;
perfis de investidor;
distribuição de aportes;
representação gráfica;
identidade visual.
A função FV foi utilizada porque representa melhor o crescimento dos aportes com juros compostos.

A aba PERFIS centraliza as regras de distribuição, enquanto a lista suspensa reduz erros e facilita a utilização.

O gráfico oferece uma referência visual que ajuda o usuário a compreender a alocação sugerida.

O resultado é uma ferramenta simples, organizada, auditável e adequada para educação financeira e planejamento preliminar de investimentos.

REFERÊNCIAS
ANBIMA — Suitability e perfil de risco:
https://www.anbima.com.br/pt_br/noticias/suitability-novas-regras-da-anbima-para-definir-perfis-de-investidor-e-de-produtos-ja-estao-valendo.htm

B3 — Fundo Incentivado de Investimento em Infraestrutura:
https://www.b3.com.br/pt_br/produtos-e-servicos/negociacao/renda-variavel/fundo-incentivado-de-investimento-em-infraestrutura-fi-infra.htm

Clube FII — Diferenças entre fundos de Tijolo, Papel e Híbridos:
https://www.clubefii.com.br/noticias/mercado/fiis-de-tijolo-papel-ou-hibrido-entenda-as-diferencas
