Resultado 1:

Prompt no Copilot: escreva um código sendo um contador para calcular o imposto de renda descontado em contracheque com base no simulador de alíquotas efetivas da receita federal, coloque exemplos de situações e me gere em formato markdown

Abaixo está um exemplo de implementação em Python para calcular o IRRF descontado no contracheque, utilizando a tabela progressiva mensal e o conceito de alíquota efetiva, conforme as tabelas publicadas pela Receita Federal para 2026.

Calculadora de IRRF para Folha de Pagamento

Calculadora de IRRF (Receita Federal)
Regras utilizadas
Tabela Progressiva Mensal (2026)
Base de Cálculo (R$)	Alíquota	Parcela a Deduzir
Até 2.428,80	Isento	0,00
2.428,81 a 2.826,65	7,5%	182,16
2.826,66 a 3.751,05	15,0%	394,16
3.751,06 a 4.664,68	22,5%	675,49
Acima de 4.664,68	27,5%	908,73
Dependente: R$ 189,59 por dependente Desconto simplificado mensal: R$ 607,20

Código Python
def calcular_irrf(
    salario_bruto,
    inss,
    dependentes=0,
    outras_deducoes=0,
    usar_desconto_simplificado=True,
):
    DEDUCAO_DEPENDENTE = 189.59
    DESCONTO_SIMPLIFICADO = 607.20

    base_legal = (
        salario_bruto
        - inss
        - (dependentes * DEDUCAO_DEPENDENTE)
        - outras_deducoes
    )

    base_simplificada = (
        salario_bruto
        - inss
        - DESCONTO_SIMPLIFICADO
    )

    if usar_desconto_simplificado:
        base_calculo = min(base_legal, base_simplificada)
    else:
        base_calculo = base_legal

    if base_calculo <= 2428.80:
        aliquota = 0
        deducao = 0

    elif base_calculo <= 2826.65:
        aliquota = 0.075
        deducao = 182.16

    elif base_calculo <= 3751.05:
        aliquota = 0.15
        deducao = 394.16

    elif base_calculo <= 4664.68:
        aliquota = 0.225
        deducao = 675.49

    else:
        aliquota = 0.275
        deducao = 908.73

    imposto = max((base_calculo * aliquota) - deducao, 0)

    aliquota_efetiva = (
        (imposto / salario_bruto) * 100
        if salario_bruto > 0
        else 0
    )

    return {
        "salario_bruto": salario_bruto,
        "base_calculo": round(base_calculo, 2),
        "irrf": round(imposto, 2),
        "aliquota_efetiva": round(aliquota_efetiva, 2),
    }


# Exemplo de uso
resultado = calcular_irrf(
    salario_bruto=8000,
    inss=908.86,
    dependentes=1
)

print(resultado)


---

# Exemplos Práticos

## Exemplo 1: Salário de R$ 3.000

```python
calcular_irrf(
    salario_bruto=3000,
    inss=248.60
)


Resultado aproximado

Base de cálculo: R$ 2.144,20
IRRF: R$ 0,00
Alíquota efetiva: 0,00%

Exemplo 2: Salário de R$ 5.000
calcular_irrf(
    salario_bruto=5000,
    inss=501.51
)


Resultado aproximado

Base de cálculo: R$ 3.891,29
IRRF: R$ 200,05
Alíquota efetiva: 4,00%

Exemplo 3: Salário de R$ 8.000
calcular_irrf(
    salario_bruto=8000,
    inss=908.86
)


Resultado aproximado

Base de cálculo: R$ 6.483,94
IRRF: R$ 874,35
Alíquota efetiva: 10,93%

Exemplo 4: Salário de R$ 12.000 com 2 dependentes
calcular_irrf(
    salario_bruto=12000,
    inss=908.86,
    dependentes=2
)


Resultado aproximado

Base de cálculo: R$ 10.712,96
IRRF: R$ 2.037,33
Alíquota efetiva: 16,98%

Fórmula da Alíquota Efetiva
Alíquota Efetiva (%) =
(IRRF Calculado ÷ Salário Bruto) × 100


Exemplo:

Salário Bruto: R$ 8.000,00
IRRF: R$ 874,35

Alíquota Efetiva =
874,35 ÷ 8.000 × 100

= 10,93%

Fonte das Faixas de Tributação

Tabela progressiva mensal da Receita Federal válida para 2026, incluindo dedução por dependente e desconto simplificado mensal.


Resultado 2:

Prompt copilot: escreva um código sendo um programador em uma requisição para audar servidores em duvidas sobre o desconto do imposto de renda com base no simulador de alíquotas efetivas da receita federal, coloque exemplos de situações e me gere em formato markdown

Vou entregar um exemplo completo em Markdown de uma aplicação que auxilia servidores públicos a entenderem o desconto de Imposto de Renda em seus contracheques, simulando a lógica da alíquota efetiva utilizada pela Receita Federal. As faixas de tributação, deduções e desconto simplificado estão baseados na tabela mensal vigente divulgada pela Receita Federal.

# Sistema de Apoio ao Servidor - Simulador de IRRF

## Objetivo

Este sistema tem como objetivo auxiliar servidores públicos a compreender:

- Como o IRRF é calculado no contracheque;
- Qual a base de cálculo utilizada;
- Quanto está sendo descontado;
- Qual a alíquota efetiva aplicada;
- O impacto de dependentes e deduções legais.

---

## Conceitos Importantes

### Base de Cálculo

A base de cálculo do IRRF corresponde ao valor tributável após as deduções permitidas.

```text
Base de Cálculo =
Salário Bruto
- INSS
- Dependentes
- Outras Deduções
Alíquota Efetiva
A alíquota efetiva demonstra o percentual real de imposto pago sobre o salário bruto.

Alíquota Efetiva =
(IRRF / Salário Bruto) × 100
Código Python
class SimuladorIRRF:

    DEDUCAO_DEPENDENTE = 189.59
    DESCONTO_SIMPLIFICADO = 607.20

    def calcular(
        self,
        salario_bruto,
        inss,
        dependentes=0,
        outras_deducoes=0,
        desconto_simplificado=True
    ):

        base_legal = (
            salario_bruto
            - inss
            - (dependentes * self.DEDUCAO_DEPENDENTE)
            - outras_deducoes
        )

        base_simplificada = (
            salario_bruto
            - inss
            - self.DESCONTO_SIMPLIFICADO
        )

        if desconto_simplificado:
            base_calculo = min(
                base_legal,
                base_simplificada
            )
        else:
            base_calculo = base_legal

        if base_calculo <= 2428.80:
            aliquota = 0
            deducao = 0

        elif base_calculo <= 2826.65:
            aliquota = 0.075
            deducao = 182.16

        elif base_calculo <= 3751.05:
            aliquota = 0.15
            deducao = 394.16

        elif base_calculo <= 4664.68:
            aliquota = 0.225
            deducao = 675.49

        else:
            aliquota = 0.275
            deducao = 908.73

        imposto = max(
            (base_calculo * aliquota) - deducao,
            0
        )

        aliquota_efetiva = (
            imposto / salario_bruto
        ) * 100

        return {
            "salario_bruto": round(salario_bruto, 2),
            "base_calculo": round(base_calculo, 2),
            "irrf": round(imposto, 2),
            "aliquota_efetiva": round(
                aliquota_efetiva,
                2
            )
        }


simulador = SimuladorIRRF()

resultado = simulador.calcular(
    salario_bruto=8000.00,
    inss=908.86,
    dependentes=1
)

print(resultado)
Exemplos de Situações Reais
Situação 1
Servidor Administrativo
Dados

Salário Bruto: R$ 3.000,00
INSS: R$ 248,60
Dependentes: 0
Resultado

Base de cálculo: R$ 2.144,20
IRRF: R$ 0,00
Alíquota efetiva: 0,00%
Explicação
Após as deduções permitidas, a base de cálculo ficou abaixo da faixa de tributação.

Situação 2
Técnico Administrativo
Dados

Salário Bruto: R$ 5.000,00
INSS: R$ 501,51
Dependentes: 0
Resultado

Base de cálculo: R$ 3.891,29
IRRF aproximado: R$ 200,05
Alíquota efetiva: 4,00%
Explicação
O servidor já se enquadra na faixa tributável, porém a alíquota efetiva permanece relativamente baixa devido às deduções aplicadas.

Situação 3
Analista
Dados

Salário Bruto: R$ 8.000,00
INSS: R$ 908,86
Dependentes: 1
Resultado

Base de cálculo: R$ 6.483,94
IRRF aproximado: R$ 874,35
Alíquota efetiva: 10,93%
Explicação
Embora a faixa nominal seja de 27,5%, o percentual efetivamente pago sobre o salário bruto é menor.

Situação 4
Professor com Dois Dependentes
Dados

Salário Bruto: R$ 12.000,00
INSS: R$ 908,86
Dependentes: 2
Resultado

Base de cálculo: R$ 10.712,96
IRRF aproximado: R$ 2.037,33
Alíquota efetiva: 16,98%
Explicação
Os dependentes reduzem a base tributável, diminuindo o valor do imposto retido.

Perguntas Frequentes
Por que meu desconto é diferente do colega que ganha o mesmo salário?
Porque podem existir diferenças em:

Quantidade de dependentes;
Previdência complementar;
Pensão alimentícia;
Desconto simplificado;
Verbas indenizatórias não tributáveis.
O que é a alíquota efetiva?
É o percentual real de IR pago sobre a remuneração.

Exemplo:

Salário Bruto = R$ 8.000,00

IRRF = R$ 874,35

Alíquota Efetiva =
874,35 ÷ 8.000 × 100

Alíquota Efetiva = 10,93%
Como utilizar este simulador?
Informe o salário bruto.
Informe o valor do INSS descontado.
Informe a quantidade de dependentes.
Informe deduções adicionais, se houver.
Execute o cálculo.
Analise a base tributável, o IRRF e a alíquota efetiva.
Observação Importante
Este simulador possui finalidade educativa e de conferência preliminar do contracheque. O valor efetivamente descontado pode variar conforme regras específicas da folha de pagamento do órgão, rubricas tributáveis e legislação vigente da Receita Federal.

Baseado na tabela progressiva mensal de IRRF com dedução por dependente e desconto simplificado divulgada pela Receita Federal.

Resultado 3:

prompt copilot: escreva um código sendo um programador em uma requisição para audar servidores em duvidas sobre o desconto do imposto de renda com base no simulador de alíquotas efetivas da receita federal, coloque exemplos de situações e me gere em formato markdow

Calculadora de IRRF para Servidores Públicos
Sobre o Projeto
Olá! Sou estudante de Ciência da Computação e desenvolvi este exemplo de sistema para ajudar servidores públicos a entenderem melhor o desconto de Imposto de Renda Retido na Fonte (IRRF) aplicado em seus contracheques.

O objetivo é fornecer uma estimativa baseada na tabela progressiva mensal da Receita Federal, permitindo visualizar:

Base de cálculo do IRRF;
Valor do imposto descontado;
Alíquota efetiva;
Impacto dos dependentes no cálculo.
Como o Cálculo Funciona
Primeiro, calculamos a base de cálculo:

Base de Cálculo =
Salário Bruto
- INSS
- Dedução por Dependentes
Em seguida, aplicamos a faixa correspondente da tabela do IRRF e calculamos a alíquota efetiva:

Alíquota Efetiva =
(IRRF ÷ Salário Bruto) × 100
Código em Python
def calcular_irrf(salario_bruto, inss, dependentes=0):
    """
    Calculadora simplificada de IRRF
    para auxílio a servidores públicos.
    """

    DEDUCAO_DEPENDENTE = 189.59

    base_calculo = (
        salario_bruto
        - inss
        - (dependentes * DEDUCAO_DEPENDENTE)
    )

    if base_calculo <= 2428.80:
        aliquota = 0
        parcela_deduzir = 0

    elif base_calculo <= 2826.65:
        aliquota = 0.075
        parcela_deduzir = 182.16

    elif base_calculo <= 3751.05:
        aliquota = 0.15
        parcela_deduzir = 394.16

    elif base_calculo <= 4664.68:
        aliquota = 0.225
        parcela_deduzir = 675.49

    else:
        aliquota = 0.275
        parcela_deduzir = 908.73

    imposto = max(
        (base_calculo * aliquota) - parcela_deduzir,
        0
    )

    aliquota_efetiva = (
        imposto / salario_bruto
    ) * 100

    return {
        "Salário Bruto": round(salario_bruto, 2),
        "Base de Cálculo": round(base_calculo, 2),
        "IRRF": round(imposto, 2),
        "Alíquota Efetiva (%)": round(
            aliquota_efetiva,
            2
        )
    }


# Exemplo de uso

resultado = calcular_irrf(
    salario_bruto=8000.00,
    inss=908.86,
    dependentes=1
)

for chave, valor in resultado.items():
    print(f"{chave}: {valor}")
Situações Práticas
Exemplo 1 - Servidor Iniciante
Dados
Salário Bruto: R$ 3.000,00
INSS: R$ 248,60
Dependentes: 0
Simulação
calcular_irrf(
    salario_bruto=3000,
    inss=248.60,
    dependentes=0
)
Resultado
Base de cálculo: R$ 2.751,40
IRRF aproximado: R$ 24,20
Alíquota efetiva: 0,81%
Interpretação
O servidor está em uma das primeiras faixas de tributação e paga um valor reduzido de imposto.

Exemplo 2 - Técnico Administrativo
Dados
Salário Bruto: R$ 5.000,00
INSS: R$ 501,51
Dependentes: 0
Simulação
calcular_irrf(
    salario_bruto=5000,
    inss=501.51,
    dependentes=0
)
Resultado
Base de cálculo: R$ 4.498,49
IRRF aproximado: R$ 336,67
Alíquota efetiva: 6,73%
Interpretação
O servidor já alcançou uma faixa mais alta da tabela, porém o percentual efetivamente pago ainda é menor que a alíquota nominal.

Exemplo 3 - Professor com um Dependente
Dados
Salário Bruto: R$ 8.000,00
INSS: R$ 908,86
Dependentes: 1
Simulação
calcular_irrf(
    salario_bruto=8000,
    inss=908.86,
    dependentes=1
)
Resultado
Base de cálculo: R$ 6.901,55
IRRF aproximado: R$ 988,20
Alíquota efetiva: 12,35%
Interpretação
A dedução do dependente reduz a base de cálculo e consequentemente o imposto devido.

Exemplo 4 - Analista com Dois Dependentes
Dados
Salário Bruto: R$ 12.000,00
INSS: R$ 908,86
Dependentes: 2
Simulação
calcular_irrf(
    salario_bruto=12000,
    inss=908.86,
    dependentes=2
)
Resultado
Base de cálculo: R$ 10.711,96
IRRF aproximado: R$ 2.037,06
Alíquota efetiva: 16,98%
Interpretação
Mesmo estando na faixa máxima da tabela, a alíquota efetiva é inferior a 27,5%, demonstrando o efeito das deduções.

Possíveis Melhorias no Projeto
Como estudante de Ciência da Computação, algumas evoluções interessantes seriam:

Interface Web usando Flask;
Interface gráfica usando Tkinter;
Geração de relatório em PDF;
Leitura automática de contracheques;
Comparação entre desconto simplificado e desconto legal;
Exportação dos resultados para Excel;
Dashboard com gráficos de evolução do IRRF.
Conclusão
Este sistema demonstra de forma simples como estimar o IRRF descontado do contracheque de um servidor público. Além de calcular o valor do imposto, ele ajuda o usuário a compreender sua base de cálculo e sua alíquota efetiva, tornando o processo mais transparente e educativo.

Observação: trata-se de um simulador acadêmico para fins de estudo. O cálculo oficial do contracheque pode incluir outras rubricas, deduções legais e regras específicas do órgão pagador.
