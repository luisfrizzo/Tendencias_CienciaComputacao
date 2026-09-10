# Atividade - Refinamento de Prompts

## Identificação

- **Nomes:** João Felipe soares silva e Luís Fernando Figueiredo Frizzo
- **Turma:** Tendências em Ciência da Computação - 2267195 
- **Data:** 09/09/2026
- **Ferramenta de IA utilizada:** ChatGPT

---

# Problema escolhido

## Contexto

JavaScript é uma das principais linguagens utilizadas no desenvolvimento de aplicações web. Porém, estudantes iniciantes podem ter dificuldades para compreender como melhorar um código que funciona, mas apresenta problemas de organização, validação ou boas práticas.

Para esta atividade, foi escolhido um problema relacionado à análise e melhoria de um código JavaScript simples, considerando um estudante que está começando a aprender programação.

## Problema

Como utilizar uma Inteligência Artificial Generativa para identificar problemas e sugerir melhorias em um código JavaScript escrito por um estudante iniciante?

## Objetivo

Investigar como o refinamento de prompts pode melhorar a qualidade, clareza e utilidade da resposta da IA na análise de um código JavaScript.

---

# Prompt 1 - Versão inicial

## Prompt

```javascript
Melhore este código JavaScript:

let nome = prompt("Digite seu nome");
let idade = prompt("Digite sua idade");

if (idade >= 18) {
    alert(nome + " é maior de idade");
} else {
    alert(nome + " é menor de idade");
}
```

## Resultado

O código pode ser melhorado principalmente na organização e na conversão da idade para número.

Uma versão melhor seria:

```javascript
let nome = prompt("Digite seu nome");
let idade = Number(prompt("Digite sua idade"));

if (idade >= 18) {
    alert(nome + " é maior de idade");
} else {
    alert(nome + " é menor de idade");
}
```

A conversão com `Number()` garante que o valor da idade seja tratado como número.

Também é possível utilizar `const` para valores que não serão alterados:

```javascript
const nome = prompt("Digite seu nome");
const idade = Number(prompt("Digite sua idade"));

if (idade >= 18) {
    alert(`${nome} é maior de idade`);
} else {
    alert(`${nome} é menor de idade`);
}
```

## Análise

### O que funcionou?

A IA identificou uma melhoria importante no código, principalmente relacionada à conversão da idade para número. Também apresentou uma alternativa utilizando `const` e template strings.

### O que faltou?

O prompt não informou que a resposta deveria ser voltada para um estudante iniciante. Também não pediu uma explicação detalhada dos problemas encontrados.

### O que ficou genérico?

A expressão "melhore este código" é muito ampla. A IA precisou decidir sozinha quais aspectos deveriam ser considerados como melhoria.

### O que poderia ser melhor?

Seria melhor informar:

- o nível do estudante;
- quais aspectos devem ser analisados;
- que cada alteração deve ser explicada;
- quais boas práticas devem ser consideradas;
- um formato específico para apresentar a resposta.

---

# Prompt 2 - Primeiro refinamento

## Alterações realizadas

- **Papel:** Professor de programação especializado em JavaScript.
- **Contexto:** Estudante iniciante de Ciência da Computação.
- **Objetivo:** Identificar problemas e melhorar o código.
- **Público:** Estudantes que estão começando a estudar JavaScript.
- **Formato:** Explicação organizada por tópicos e código corrigido.
- **Restrições:** Não utilizar recursos avançados de JavaScript.
- **Critérios:** A solução deve ser simples e fácil de compreender.

## Prompt

```text
Atue como professor de programação especializado em JavaScript.

CONTEXTO:
O código foi escrito por um estudante iniciante de Ciência
da Computação que está começando a estudar JavaScript.

CÓDIGO:

let nome = prompt("Digite seu nome");
let idade = prompt("Digite sua idade");

if (idade >= 18) {
    alert(nome + " é maior de idade");
} else {
    alert(nome + " é menor de idade");
}

TAREFA:
Analise o código e identifique possíveis problemas ou
melhorias.

Explique cada alteração de maneira simples, informando
por que ela é necessária.

Depois apresente uma versão melhorada do código.

FORMATO:
Organize a resposta em:
1. Problemas encontrados;
2. Explicação das melhorias;
3. Código melhorado;
4. Resumo do que foi aprendido.

RESTRIÇÕES:
- Considere que o estudante é iniciante;
- Não utilize recursos avançados de JavaScript;
- Não altere o objetivo original do programa.
```

## Resultado

### 1. Problemas encontrados

O código funciona para uma situação simples, mas possui alguns pontos que podem ser melhorados:

- `prompt()` retorna um texto;
- a idade deveria ser convertida explicitamente para número;
- é possível utilizar `const`, pois os valores não são alterados;
- a concatenação pode ser substituída por template strings.

### 2. Explicação das melhorias

A função `prompt()` retorna uma string. Por isso, utilizar `Number()` deixa explícito que a idade deve ser tratada como número.

Também podemos utilizar `const`, pois `nome` e `idade` não precisam receber novos valores.

Template strings permitem escrever a mensagem de forma mais organizada.

### 3. Código melhorado

```javascript
const nome = prompt("Digite seu nome");
const idade = Number(prompt("Digite sua idade"));

if (idade >= 18) {
    alert(`${nome} é maior de idade`);
} else {
    alert(`${nome} é menor de idade`);
}
```

### 4. Resumo

As principais melhorias foram a conversão da idade para número, o uso de `const` e uma forma mais organizada de montar as mensagens.

---

# Comparação

| Critério | Prompt 1 | Prompt 2 |
|---|---:|---:|
| Clareza | 3 | 5 |
| Precisão | 3 | 5 |
| Relevância | 3 | 5 |
| Organização | 3 | 5 |
| Adequação ao público | 2 | 5 |
| Atendimento ao objetivo | 3 | 5 |
| Utilidade prática | 3 | 5 |
| **Total** | **20** | **35** |

## Análise das melhorias

O segundo prompt apresentou um resultado melhor porque forneceu mais informações relevantes para a IA.

No primeiro prompt, apenas foi solicitado que o código fosse melhorado. Dessa forma, a IA precisou decidir quais aspectos deveriam ser modificados.

No segundo prompt, foram definidos o papel da IA, o contexto, o público, o objetivo, o formato e as restrições. Isso fez com que a resposta fosse mais organizada e adequada para um estudante iniciante.

---

# Prompt 3 - Segundo refinamento

## O que ainda precisava melhorar?

Apesar da segunda resposta ter sido mais organizada, ainda havia alguns pontos que poderiam ser melhorados.

O código não possui validação para situações como:

- usuário não informar o nome;
- usuário cancelar o `prompt`;
- usuário informar uma idade inválida;
- usuário informar um número negativo.

Além disso, como o objetivo é aprendizado, seria interessante pedir que a IA explicasse os possíveis erros sem simplesmente entregar uma solução muito complexa.

## Hipótese de melhoria

Acredito que a resposta ficará melhor porque, além de solicitar melhorias no código, o novo prompt definirá casos de entrada inválidos e pedirá que a IA explique como tratar esses casos de maneira simples, mantendo o código adequado para um estudante iniciante.

## Prompt

```text
Atue como professor de programação especializado em JavaScript
e ensino para estudantes iniciantes.

CONTEXTO:
O código abaixo foi desenvolvido por um estudante do primeiro
semestre de Ciência da Computação que está começando a aprender
JavaScript.

CÓDIGO:

let nome = prompt("Digite seu nome");
let idade = prompt("Digite sua idade");

if (idade >= 18) {
    alert(nome + " é maior de idade");
} else {
    alert(nome + " é menor de idade");
}

OBJETIVO:
Melhorar o código sem modificar seu objetivo principal,
fazendo com que ele fique mais seguro, organizado e fácil
de compreender.

TAREFA:
1. Identifique os problemas do código original;
2. Explique cada problema em linguagem simples;
3. Verifique problemas relacionados ao tipo de dado da idade;
4. Considere entradas inválidas;
5. Apresente uma versão corrigida;
6. Explique as alterações realizadas;
7. Apresente dois exemplos de entrada e saída;
8. Aponte uma melhoria que poderia ser feita no futuro.

FORMATO:
Organize a resposta utilizando subtítulos.

Apresente uma tabela contendo:
Problema | Causa | Consequência | Solução

RESTRIÇÕES:
- O público é iniciante;
- Não utilize bibliotecas externas;
- Não utilize conceitos avançados;
- Não altere o objetivo principal do programa;
- Explique todos os termos técnicos utilizados;
- O código deve permanecer simples.

CRITÉRIO DE QUALIDADE:
Ao final, um estudante iniciante deve conseguir explicar
com suas próprias palavras quais eram os principais problemas
do código original e por que as alterações foram realizadas.
```

## Resultado

### Problemas encontrados

| Problema | Causa | Consequência | Solução |
|---|---|---|---|
| Idade recebida como texto | `prompt()` retorna string | Pode causar comportamentos inesperados | Utilizar `Number()` |
| Entrada inválida | Não existe validação | O programa pode apresentar resultado incorreto | Verificar se a idade é válida |
| Nome vazio | Não existe validação | A mensagem pode ficar incompleta | Verificar o nome informado |
| Variáveis podem ser constantes | Os valores não são alterados | O código pode ficar menos claro | Utilizar `const` |

### Código corrigido

```javascript
const nome = prompt("Digite seu nome");
const idade = Number(prompt("Digite sua idade"));

if (!nome) {
    alert("Nome não informado.");
} else if (isNaN(idade) || idade < 0) {
    alert("Digite uma idade válida.");
} else if (idade >= 18) {
    alert(`${nome} é maior de idade.`);
} else {
    alert(`${nome} é menor de idade.`);
}
```

### Explicação

O primeiro problema é que `prompt()` retorna um texto. Por isso, foi utilizado `Number()` para transformar o valor informado em número.

Também foi utilizada uma verificação com `isNaN()` para identificar quando a idade informada não representa um número válido.

A condição `idade < 0` impede que uma idade negativa seja considerada válida.

A verificação `!nome` permite identificar quando o usuário não informou um nome.

O uso de `const` indica que os valores não serão alterados posteriormente.

### Exemplo 1

**Entrada:**

```text
Nome: João
Idade: 22
```

**Saída:**

```text
João é maior de idade.
```

### Exemplo 2

**Entrada:**

```text
Nome: Maria
Idade: abc
```

**Saída:**

```text
Digite uma idade válida.
```

### Melhoria futura

Uma melhoria futura seria substituir os `prompt()` e `alert()` por uma interface HTML com campos de entrada e botões, tornando o programa mais adequado para uma aplicação web.

---

# Comparação final

| Critério | Prompt 1 | Prompt 2 | Prompt 3 |
|---|---:|---:|---:|
| Clareza | 3 | 5 | 5 |
| Precisão | 3 | 5 | 5 |
| Relevância | 3 | 5 | 5 |
| Organização | 3 | 5 | 5 |
| Adequação ao público | 2 | 5 | 5 |
| Atendimento ao objetivo | 3 | 5 | 5 |
| Utilidade prática | 3 | 5 | 5 |
| **Total** | **20** | **35** | **35** |

## Qual foi a melhoria?

A principal evolução aconteceu entre o Prompt 1 e o Prompt 2.

O Prompt 1 apresentava apenas a tarefa de melhorar o código. Já o Prompt 2 definiu o papel da IA, o contexto, o público, o objetivo, o formato e as restrições.

O Prompt 3 manteve essas características e acrescentou critérios mais específicos, principalmente a análise de entradas inválidas e a explicação dos problemas.

Assim, o resultado passou de uma simples sugestão de código para uma análise mais adequada ao processo de aprendizagem.

> **Qual modificação teve maior impacto no resultado?**

A definição do **contexto e do público** teve grande impacto, pois fez com que a IA apresentasse as explicações considerando um estudante iniciante. A definição do formato também melhorou bastante a organização da resposta.

---

# Validação

A qualidade da resposta foi analisada verificando se:

- a solução continuava utilizando JavaScript;
- o objetivo original do programa foi mantido;
- os conceitos utilizados existem na linguagem;
- `prompt()` realmente retorna uma string;
- `Number()` pode ser utilizado para conversão numérica;
- `isNaN()` pode ser utilizado para verificar valores que não representam números;
- o código apresentado é compatível com JavaScript;
- as melhorias realmente solucionam os problemas identificados.

Também foi analisado se a resposta estava adequada ao nível de um estudante iniciante.

A validação é importante porque uma resposta da IA pode parecer correta e ainda conter erros técnicos. A própria atividade destaca que uma resposta bem escrita não é necessariamente correta e recomenda verificar conceitos, dados e informações antes de utilizar o conteúdo.

---

# Reflexão

## 1. Qual foi a principal diferença entre os prompts?

A principal diferença foi a quantidade e a qualidade das informações fornecidas à IA.

O primeiro prompt apenas pediu para melhorar o código. Os prompts seguintes explicaram o contexto, o público, o objetivo, o formato e as restrições.

## 2. Quais elementos tiveram maior impacto?

Os elementos que tiveram maior impacto foram o **contexto**, o **público**, o **objetivo**, o **formato** e os **critérios de qualidade**.

Esses elementos diminuíram a quantidade de informações que a IA precisava interpretar ou imaginar.

## 3. Um prompt maior é necessariamente melhor?

Não. Um prompt maior não é necessariamente melhor.

O mais importante é fornecer informações relevantes para o objetivo. Um prompt curto, mas específico, pode produzir uma resposta melhor do que um prompt longo e genérico.

## 4. O que ocorre quando o objetivo não é claro?

Quando o objetivo não está claro, a IA precisa interpretar o que o usuário deseja. Isso pode gerar uma resposta genérica, incompleta ou diferente do resultado esperado.

## 5. Quais informações são indispensáveis?

As informações mais importantes são:

- objetivo;
- contexto;
- público;
- tarefa;
- formato esperado;
- restrições;
- critérios de qualidade.

Esses elementos ajudam a reduzir ambiguidades.

## 6. Como essa habilidade pode ser utilizada profissionalmente?

A habilidade pode ser utilizada por profissionais de Ciência da Computação para auxiliar na programação, documentação, análise de códigos, criação de testes, estudos, resolução de problemas e comparação de tecnologias.

Também pode ajudar o profissional a obter respostas mais específicas e úteis de ferramentas de IA.

## 7. Quais riscos existem ao confiar automaticamente na IA?

A IA pode apresentar informações incorretas, conceitos equivocados, referências inexistentes ou soluções que parecem funcionar, mas possuem problemas.

Por isso, o usuário precisa analisar e validar as respostas antes de utilizá-las.

## 8. Houve alguma situação em que o Prompt 3 ficou pior que o Prompt 2?

Não houve uma piora significativa. O Prompt 3 manteve as características positivas do Prompt 2 e adicionou novas informações.

Porém, existe o risco de adicionar instruções demais e tornar o prompt desnecessariamente complexo. Por isso, é importante adicionar apenas informações que realmente contribuam para o objetivo.

## 9. Existe um ponto em que adicionar mais instruções começa a prejudicar a resposta?

Sim. Quando existem muitas instruções desnecessárias, contraditórias ou pouco relacionadas ao objetivo, elas podem dificultar a interpretação da tarefa.

Por isso, refinar um prompt não significa simplesmente adicionar cada vez mais informações.

## 10. O que você faria para verificar se a resposta tecnicamente está correta?

Eu verificaria a documentação da linguagem, testaria o código em um ambiente JavaScript e compararia a explicação da IA com fontes confiáveis.

Também faria diferentes testes de entrada para verificar se o programa realmente apresenta os resultados esperados.

---

# Take Away

> **"Um bom prompt não é simplesmente um prompt longo. Ele precisa ser claro, específico, contextualizado e direcionado ao objetivo que se deseja alcançar."**

---

# Cinco recomendações

1. **Defina claramente o objetivo** antes de escrever o prompt.
2. **Informe o contexto e o público** para adequar a resposta.
3. **Especifique o formato desejado** para organizar melhor o resultado.
4. **Adicione restrições relevantes** para evitar respostas inadequadas.
5. **Sempre analise e valide a resposta da IA** antes de utilizá-la.

---

# Desafio final

Imagine que um colega diga:

> "Meu prompt não funcionou. A IA respondeu errado."

Antes de modificar o prompt, eu faria as seguintes perguntas:

1. **O objetivo do prompt estava claramente definido?**
2. **As informações fornecidas à IA estavam corretas e completas?**
3. **O prompt explicou o contexto e o público da resposta?**
4. **A resposta da IA foi realmente testada ou apenas considerada errada?**
5. **O problema está no prompt ou existe algum erro nas informações utilizadas pela IA?**

Essas perguntas ajudam a descobrir se o problema está realmente na formulação do prompt ou na resposta produzida.

---

# Conclusão

A atividade demonstrou que pequenas mudanças na formulação de um prompt podem modificar significativamente a resposta de uma Inteligência Artificial.

No primeiro prompt, a solicitação era genérica e permitia diferentes interpretações. No segundo, foram adicionados contexto, público, objetivo, formato e restrições. No terceiro, foram acrescentados critérios ainda mais específicos relacionados à validação do código e ao processo de aprendizagem.

Dessa forma, o refinamento de prompts pode tornar as respostas mais claras, precisas, organizadas e úteis.

Entretanto, o refinamento não elimina a necessidade de análise humana. A resposta produzida pela IA deve ser verificada antes de ser utilizada.

O processo pode ser resumido em:

```text
PROMPT
   ↓
RESPOSTA
   ↓
ANÁLISE
   ↓
IDENTIFICAÇÃO DE LIMITAÇÕES
   ↓
REFINAMENTO
   ↓
NOVA RESPOSTA
   ↓
COMPARAÇÃO
   ↓
VALIDAÇÃO
```

O principal aprendizado foi que **um bom prompt não é necessariamente um prompt longo, mas um prompt que fornece as informações necessárias para orientar a IA de forma clara em direção ao objetivo desejado**.
