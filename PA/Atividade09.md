# Aula de Lógica de Programação — JavaScript
## Operadores, estruturas de decisão e estruturas de repetição

**Modalidade:** Aula remota — estudo e prática individual

**Objetivo:** Aprender a utilizar operadores e estruturas de controle para desenvolver programas capazes de tomar decisões e repetir tarefas.

## 1. Orientações importantes

Esta aula é para **estudar, testar o código e praticar**.

**Os exercícios NÃO valem nota.** Eles não são uma atividade avaliativa e não precisam ser feitos apenas para entregar alguma coisa.

A proposta é que vocês realmente aprendam a resolver os problemas utilizando a lógica de programação.

Não utilizem a Inteligência Artificial simplesmente para obter as respostas prontas. Se fizerem isso, poderão até conseguir resolver os exercícios, mas não desenvolverão a habilidade necessária para programar sozinhos.

**Atenção: na nossa próxima aula presencial, vocês precisarão utilizar os conceitos estudados aqui para realizar uma atividade prática.** Por isso, aproveitem esta aula remota para estudar, testar os exemplos, cometer erros, corrigir o código e entender como cada estrutura funciona.

Vocês já conhecem variáveis (`var` e `let`), tipos de dados, objetos, entrada e saída de dados com `prompt()` e `alert()`, além de `document.getElementById()`, `.value`, `.innerHTML` e `.innerText`.

Agora vamos aprender a controlar o comportamento de um programa.

---

# Parte 1 — Operadores em JavaScript

Os operadores permitem realizar cálculos, comparar valores e combinar condições.

## 2. Operadores aritméticos

São utilizados para realizar operações matemáticas.

| Operador | Operação | Exemplo | Resultado |
|---|---|---|---|
| `+` | Adição | `10 + 3` | `13` |
| `-` | Subtração | `10 - 3` | `7` |
| `*` | Multiplicação | `10 * 3` | `30` |
| `/` | Divisão | `10 / 2` | `5` |
| `%` | Resto da divisão | `10 % 3` | `1` |
| `**` | Potenciação | `2 ** 3` | `8` |

Exemplo:

```javascript
let numero1 = 10;
let numero2 = 3;

let soma = numero1 + numero2;
let resto = numero1 % numero2;

alert("Soma: " + soma);
alert("Resto: " + resto);
```

O operador `%` é especialmente importante. Ele permite verificar, por exemplo, se um número é par ou ímpar.

```javascript
let numero = 8;

alert(numero % 2);
```

O resultado será `0`, porque 8 é divisível por 2 sem deixar resto.

Se o resultado de `numero % 2` for diferente de zero, o número é ímpar.

## 3. Operadores relacionais

Os operadores relacionais comparam dois valores. O resultado de uma comparação é sempre um valor booleano: `true` (verdadeiro) ou `false` (falso).

| Operador | Significado | Exemplo | Resultado |
|---|---|---|---|
| `>` | Maior que | `10 > 5` | `true` |
| `<` | Menor que | `3 < 2` | `false` |
| `>=` | Maior ou igual a | `5 >= 5` | `true` |
| `<=` | Menor ou igual a | `4 <= 3` | `false` |
| `==` | Igualdade de valor, com conversão de tipo | `5 == "5"` | `true` |
| `===` | Igualdade estrita, incluindo o tipo | `5 === "5"` | `false` |
| `!=` | Diferente, com conversão de tipo | `5 != "5"` | `false` |
| `!==` | Diferente em valor ou tipo | `5 !== "5"` | `true` |

**Recomendação:** prefira `===` e `!==` nas comparações, pois deixam explícito que o tipo dos valores também importa.

Observe:

```javascript
let idade = 18;

console.log(idade >= 18);
console.log(idade < 18);
console.log(idade === 18);
```

Os resultados serão, respectivamente, `true`, `false` e `true`.

## 4. Operadores lógicos

Os operadores lógicos permitem combinar condições.

### Operador E — `&&`

Todas as condições precisam ser verdadeiras.

```javascript
let idade = 20;
let temIngresso = true;

let podeEntrar = idade >= 18 && temIngresso === true;

alert(podeEntrar);
```

O resultado será `true`, porque a pessoa tem pelo menos 18 anos e possui ingresso.

Se qualquer uma das condições for falsa, o resultado será falso.

### Operador OU — `||`

Basta que pelo menos uma condição seja verdadeira.

```javascript
let temCarteirinha = false;
let temConvite = true;

let podeParticipar = temCarteirinha || temConvite;

alert(podeParticipar);
```

O resultado será `true`, pois a pessoa tem convite.

### Operador NÃO — `!`

Inverte um valor lógico: verdadeiro passa a falso, e falso passa a verdadeiro.

```javascript
let estaBloqueado = false;

alert(!estaBloqueado);
```

O resultado será `true`.

### Resumo dos operadores lógicos

| Expressão | Resultado |
|---|---|
| `true && true` | `true` |
| `true && false` | `false` |
| `true || false` | `true` |
| `false || false` | `false` |
| `!true` | `false` |
| `!false` | `true` |

### Exemplo: acesso a um sistema

Imagine que um usuário só pode acessar um sistema se tiver 18 anos ou mais e estiver com a conta ativa.

```javascript
let idade = 25;
let contaAtiva = true;

let acessoPermitido = idade >= 18 && contaAtiva;

alert(acessoPermitido);
```

Experimente alterar a idade e o valor de `contaAtiva`. Observe quando o acesso será permitido ou negado.

---

# Parte 2 — Estruturas de decisão

Até agora, os programas executavam as instruções em sequência. Com as estruturas de decisão, podemos escolher quais instruções serão executadas dependendo de uma condição.

## 5. Estrutura `if`

O `if` executa um bloco de código somente quando uma condição é verdadeira.

```javascript
let idade = 20;

if (idade >= 18) {
    alert("Você é maior de idade.");
}
```

Se a idade for menor que 18, a mensagem não será exibida.

A estrutura segue esta ideia:

```javascript
if (condicao) {
    // Código executado se a condição for verdadeira
}
```

## 6. Estrutura `if...else`

Utilizamos `else` quando precisamos definir o que acontece caso a condição seja falsa.

```javascript
let idade = 16;

if (idade >= 18) {
    alert("Maior de idade.");
} else {
    alert("Menor de idade.");
}
```

O programa escolhe um dos dois caminhos.

## 7. Estrutura `if...else if...else`

Quando existem várias possibilidades, podemos encadear condições.

Exemplo: verificar a situação de um aluno pela média.

```javascript
let media = 7;

if (media >= 9) {
    alert("Excelente!");
} else if (media >= 6) {
    alert("Aprovado.");
} else {
    alert("Precisa recuperar.");
}
```

O programa testa as condições em ordem e executa somente o primeiro bloco cuja condição seja verdadeira.

Por isso, a ordem das condições é importante.

## 8. Cuidado com os dados recebidos pelo `prompt()`

O `prompt()` retorna texto. Mesmo quando o usuário digita um número, o valor recebido inicialmente é uma string.

Observe este exemplo:

```javascript
let idade = prompt("Digite sua idade:");

if (idade >= 18) {
    alert("Maior de idade.");
}
```

O JavaScript pode converter o texto em número durante a comparação, mas é melhor deixar a intenção explícita.

```javascript
let idade = Number(prompt("Digite sua idade:"));

if (idade >= 18) {
    alert("Maior de idade.");
} else {
    alert("Menor de idade.");
}
```

A função `Number()` converte o texto em número quando a entrada é válida.

## 9. Exemplo com formulário HTML

Vocês já aprenderam a capturar dados de campos HTML usando `.value`. Agora vamos utilizar esse conhecimento com uma estrutura de decisão.

```html
<label for="idade">Digite sua idade:</label>

<input type="number" id="idade">

<button onclick="verificarIdade()">Verificar</button>

<p id="resultado"></p>

<script>
    function verificarIdade() {
        let idade = Number(document.getElementById("idade").value);

        if (idade >= 18) {
            document.getElementById("resultado").innerText =
                "Você é maior de idade.";
        } else {
            document.getElementById("resultado").innerText =
                "Você é menor de idade.";
        }
    }
</script>
```

O que acontece nesse programa?

1. O usuário informa a idade.
2. O programa captura o conteúdo do campo.
3. O valor é convertido em número.
4. A condição é avaliada.
5. O resultado é exibido na página usando `.innerText`.

Observação: esse exemplo considera que o usuário informou uma idade válida. Posteriormente, vocês poderão acrescentar validações.

## 10. Decisões com operadores lógicos

Agora podemos combinar os conhecimentos.

Exemplo: verificar se uma pessoa pode participar de uma atividade.

```javascript
let idade = Number(prompt("Digite sua idade:"));
let autorizado = prompt("Você possui autorização? (sim/não)");

if (idade >= 16 && autorizado === "sim") {
    alert("Participação permitida.");
} else {
    alert("Participação não permitida.");
}
```

A participação exige duas condições verdadeiras: idade mínima de 16 anos e autorização igual a `"sim"`.

---

# Parte 3 — Estruturas de repetição

As estruturas de repetição permitem executar um bloco de código várias vezes sem precisar escrever as mesmas instruções repetidamente.

## 11. Estrutura `while`

O `while` repete o código enquanto a condição for verdadeira.

```javascript
let contador = 1;

while (contador <= 5) {
    console.log(contador);
    contador++;
}
```

Resultado no console:

```text
1
2
3
4
5
```

Entenda as três partes:

- `let contador = 1`: inicializa a variável.
- `contador <= 5`: define quando a repetição continua.
- `contador++`: aumenta o contador em uma unidade.

O operador `++` incrementa o valor da variável em 1.

**Atenção:** se a condição nunca se tornar falsa, o programa poderá entrar em um loop infinito.

Experimente remover temporariamente o `contador++` e pense no que aconteceria. Não deixe o navegador preso em uma repetição infinita.

## 12. Estrutura `do...while`

A diferença é que o `do...while` executa o bloco pelo menos uma vez antes de verificar a condição.

```javascript
let numero = 1;

do {
    console.log(numero);
    numero++;
} while (numero <= 5);
```

Mesmo que a condição seja falsa inicialmente, o bloco é executado uma vez.

Compare:

```javascript
let numero = 10;

while (numero <= 5) {
    console.log("While");
}
```

Esse exemplo não imprime nada.

Já o exemplo abaixo imprime `"Do while"` uma vez:

```javascript
let numero = 10;

do {
    console.log("Do while");
} while (numero <= 5);
```

## 13. Estrutura `for`

O `for` é muito utilizado quando sabemos quantas vezes queremos repetir uma operação.

```javascript
for (let contador = 1; contador <= 5; contador++) {
    console.log(contador);
}
```

A estrutura possui três partes:

```javascript
for (inicio; condicao; incremento) {
    // Instruções que serão repetidas
}
```

- **Início:** executado uma vez, antes da repetição.
- **Condição:** enquanto for verdadeira, o bloco será executado.
- **Incremento:** executado ao final de cada repetição.

### Exemplo: tabuada do 5

```javascript
let numero = 5;

for (let contador = 1; contador <= 10; contador++) {
    console.log(numero + " x " + contador + " = " + numero * contador);
}
```

O programa exibirá a tabuada do 5, de 1 a 10.

## 14. Exemplo com entrada de dados e repetição

Imagine que queremos pedir um número ao usuário e mostrar todos os números de 1 até esse valor.

```javascript
let limite = Number(prompt("Digite um número inteiro positivo:"));

for (let contador = 1; contador <= limite; contador++) {
    console.log(contador);
}
```

Se o usuário informar `4`, serão exibidos os números 1, 2, 3 e 4.

Experimente modificar o exemplo para exibir somente os números pares.

Uma dica: utilize o operador `%` para verificar o resto da divisão por 2.

## 15. Qual estrutura devo utilizar?

| Estrutura | Quando utilizar |
|---|---|
| `if` | Quando precisamos executar um código dependendo de uma condição. |
| `if...else` | Quando existem dois caminhos possíveis. |
| `if...else if...else` | Quando precisamos analisar várias possibilidades. |
| `while` | Quando repetimos enquanto uma condição for verdadeira. |
| `do...while` | Quando precisamos executar pelo menos uma vez. |
| `for` | Quando a repetição normalmente utiliza um contador ou uma quantidade conhecida de iterações. |

---

# Parte 4 — Exercícios de prática

**Reforçando: estes exercícios não valem nota.** A finalidade é desenvolver a lógica de programação para que vocês estejam preparados para a atividade da próxima aula presencial.

Não se preocupem em terminar tudo rapidamente. É melhor resolver poucos exercícios compreendendo o raciocínio do que copiar muitas respostas sem saber explicar como funcionam.

Procurem escrever o código, executar, testar valores diferentes e corrigir os erros encontrados.

## Nível 1 — Operadores e comparações

**Exercício 1 — Maior ou menor**

Solicite dois números utilizando `prompt()`.

Exiba com `alert()` qual deles é maior. Se forem iguais, informe que os números são iguais.

**Exercício 2 — Par ou ímpar**

Solicite um número inteiro e informe se ele é par ou ímpar.

Dica: utilize o operador `%`.

**Exercício 3 — Calculadora simples**

Solicite dois números e exiba:

- A soma;
- A subtração;
- A multiplicação;
- A divisão, desde que o segundo número seja diferente de zero.

**Exercício 4 — Desafio dos operadores lógicos**

Considere as variáveis:

```javascript
let idade = 17;
let temAutorizacao = true;
let acompanhado = false;
```

Sem executar o programa inicialmente, determine o resultado das expressões:

```javascript
idade >= 18
idade >= 16 && temAutorizacao
idade >= 18 || acompanhado
!temAutorizacao
```

Depois, execute os testes no console e confira suas respostas.

## Nível 2 — Estruturas de decisão

**Exercício 5 — Classificação por idade**

Solicite a idade de uma pessoa e classifique-a em uma das categorias:

- Criança: até 11 anos;
- Adolescente: de 12 a 17 anos;
- Adulto: de 18 a 59 anos;
- Idoso: 60 anos ou mais.

Não esqueça de pensar em como tratar uma idade negativa.

**Exercício 6 — Média escolar**

Solicite duas notas, calcule a média e informe:

- Média igual ou superior a 6: aprovado;
- Média entre 3 e 5,99: recuperação;
- Média inferior a 3: reprovado.

Considere notas válidas de 0 a 10. Pense também em como impedir que valores fora desse intervalo sejam aceitos.

**Exercício 7 — Desconto em uma compra**

Solicite o valor de uma compra.

- Compras a partir de R$ 200,00 recebem 10% de desconto;
- Compras abaixo desse valor não recebem desconto.

Exiba o valor original, o desconto e o valor final.

**Exercício 8 — Login simplificado**

Crie duas variáveis com um usuário e uma senha previamente definidos no código.

Solicite que o usuário informe suas credenciais. Se o usuário e a senha estiverem corretos, exiba uma mensagem de sucesso. Caso contrário, informe que o acesso foi negado.

Dica: as duas informações precisam estar corretas simultaneamente.

Este é apenas um exercício didático, não um sistema de autenticação real.

## Nível 3 — Estruturas de repetição

**Exercício 9 — Contagem**

Utilize um `for` para exibir os números de 1 até 20 no console.

Depois, modifique o código para exibir somente os números pares.

**Exercício 10 — Contagem regressiva**

Solicite um número inteiro positivo e faça uma contagem regressiva até zero.

Ao final, exiba a mensagem `"Fim!"`.

**Exercício 11 — Tabuada**

Solicite um número e exiba sua tabuada de 1 a 10.

Exemplo: se o número for 3, o programa deverá apresentar os resultados de `3 x 1` até `3 x 10`.

**Exercício 12 — Soma acumulada**

Solicite 5 números ao usuário, utilizando uma estrutura de repetição.

Some os valores informados e apresente o total ao final.

Desafio adicional: calcule também a média dos cinco números.

## Nível 4 — Desafios de lógica

**Exercício 13 — Adivinhe o número**

Defina no código um número secreto entre 1 e 20.

Peça ao usuário para tentar adivinhar o número. Enquanto ele não acertar, informe se o palpite é maior ou menor que o número secreto e permita uma nova tentativa.

Quando acertar, exiba uma mensagem de parabéns.

Utilize uma estrutura de repetição e uma estrutura de decisão.

**Exercício 14 — Validação de senha**

Defina uma senha previamente no código.

Solicite a senha ao usuário. Enquanto ela estiver incorreta, permita que ele tente novamente.

Quando acertar, informe que o acesso foi autorizado.

Desafio adicional: limite o usuário a três tentativas e informe quando o acesso for bloqueado.

**Exercício 15 — Caixa eletrônico simplificado**

Considere um saldo inicial de R$ 500,00.

Apresente um menu com as opções:

1. Consultar saldo;
2. Depositar;
3. Sacar;
4. Sair.

O programa deverá repetir o menu até que o usuário escolha sair.

Regras:

- Não permitir depósitos de valores negativos ou iguais a zero;
- Não permitir saques superiores ao saldo disponível;
- Atualizar o saldo após cada operação;
- Informar quando uma opção inválida for selecionada.

Utilize as estruturas de decisão e repetição que considerar adequadas.

---

# Parte 5 — Como estudar nesta aula

Para cada exercício, siga esta sequência:

1. **Entenda o problema.** O que o programa precisa fazer?
2. **Pense na lógica.** Quais informações serão necessárias? Quais condições devem ser verificadas?
3. **Escreva o código.** Utilize as estruturas que estudamos.
4. **Execute e teste.** Experimente valores diferentes, inclusive situações que possam provocar erros.
5. **Explique o seu raciocínio.** Tente explicar por que utilizou determinado operador ou estrutura.

Se encontrar dificuldades, volte aos exemplos do material e modifique-os gradualmente.

Não é necessário resolver todos os exercícios hoje. Priorizem a compreensão dos conceitos.

## Preparação para a próxima aula presencial

Na próxima aula presencial, vocês deverão utilizar operadores, estruturas de decisão e estruturas de repetição para resolver um problema prático.

Por isso, é importante que consigam, sem simplesmente copiar um código pronto:

- Comparar valores;
- Combinar condições com `&&`, `||` e `!`;
- Utilizar `if`, `else` e `else if`;
- Repetir instruções utilizando `for` e `while`;
- Receber dados do usuário e apresentar resultados;
- Combinar decisões e repetições em um mesmo programa.

**Lembrem-se: o objetivo desta aula não é entregar exercícios. É aprender a pensar como programadores.**
