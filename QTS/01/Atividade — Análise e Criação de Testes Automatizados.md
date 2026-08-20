
# Atividade — Análise e Criação de Testes Automatizados

## 1. Tema

**Análise, compreensão e criação de testes automatizados em uma API TypeScript**

---

## 2. Objetivo da atividade

Nesta atividade, você deverá analisar os testes automatizados já existentes no sistema, compreender como eles foram estruturados, identificar o objetivo de cada teste e aprender a interpretar seus resultados.

Ao final, você deverá criar uma pequena nova funcionalidade no sistema, suficientemente simples para ser testada, e deverá criar testes automatizados capazes de demonstrar dois cenários:

- quando a funcionalidade funciona corretamente;
- quando a funcionalidade apresenta um comportamento diferente do esperado.

O objetivo não é apenas fazer o teste passar.

**O objetivo é compreender por que o teste existe, o que ele está verificando e como identificar uma falha.**

---

# 3. Conhecimentos que serão trabalhados

Ao realizar a atividade, você deverá desenvolver conhecimentos sobre:

- testes automatizados;
- estrutura de um arquivo de teste;
- organização dos testes;
- preparação dos dados para o teste;
- execução de uma função;
- comparação entre resultado esperado e resultado obtido;
- testes de sucesso;
- testes de falha;
- interpretação dos resultados apresentados pelo framework;
- identificação da causa de uma falha;
- importância dos testes para a manutenção de um sistema.

---

# 4. Parte 1 — Conhecendo a estrutura dos testes

Analise os arquivos de teste já existentes no projeto.

Observe principalmente:

- como o arquivo de teste está organizado;
- como os testes são agrupados;
- como uma função é executada;
- como os dados utilizados pelo teste são definidos;
- como o resultado esperado é informado;
- como o resultado obtido é comparado;
- como o teste informa que determinado comportamento está correto.

### Responda:

**1.** Qual framework está sendo utilizado para executar os testes automatizados?

**2.** Qual é a finalidade de um arquivo de teste dentro do projeto?

**3.** Como os testes estão organizados dentro do arquivo?

**4.** Como o teste executa a função que está sendo avaliada?

**5.** Como o teste determina qual seria o resultado correto?

**6.** Como o teste compara o resultado obtido com o resultado esperado?

**7.** Por que é importante que o teste seja capaz de verificar automaticamente o resultado, em vez de depender apenas da observação do programador?

---

# 5. Parte 2 — Compreendendo os testes existentes

Agora analise individualmente **cada teste automatizado já existente no projeto**.

Para cada teste, identifique:

1. Qual função ou comportamento está sendo testado?
2. Qual situação está sendo simulada?
3. Qual resultado era esperado?
4. Qual resultado seria considerado incorreto?
5. O que exatamente o teste está garantindo?
6. O que poderia acontecer no sistema se esse comportamento fosse alterado e não existisse esse teste?

### Produza uma tabela semelhante a esta:

| Teste | O que está sendo testado? | Situação simulada | Resultado esperado | Objetivo |
|---|---|---|---|---|
| Teste 1 | ... | ... | ... | ... |
| Teste 2 | ... | ... | ... | ... |
| Teste 3 | ... | ... | ... | ... |

**Atenção:** não copie simplesmente o código do teste.

Você deverá explicar, com suas próprias palavras, **qual problema aquele teste pretende evitar**.

---

# 6. Parte 3 — Executando os testes

Execute os testes automatizados utilizando o comando definido no projeto.

Observe atentamente o resultado apresentado pelo terminal.

Você deverá identificar:

- quantidade de testes executados;
- quantidade de testes aprovados;
- quantidade de testes que falharam;
- arquivo onde ocorreu o teste;
- identificação do teste;
- mensagem apresentada pelo framework;
- diferença entre o resultado esperado e o resultado obtido, quando houver uma falha.

### Responda:

**1.** Como você executou os testes?

**2.** Como é possível saber que todos os testes foram executados com sucesso?

**3.** Como o resultado apresentado pelo terminal informa que um teste falhou?

**4.** Quando um teste falha, quais informações podem ser utilizadas para descobrir o problema?

**5.** Uma falha no teste significa necessariamente que existe um erro no teste? Explique.

---

# 7. Parte 4 — Provocando uma falha

Nesta etapa você deverá experimentar uma situação importante.

Escolha um dos testes existentes e altere temporariamente alguma informação relacionada ao resultado esperado.

Por exemplo, se o teste espera:

```text
10
```

faça temporariamente o teste esperar:

```text
20
```

Execute novamente os testes.

### Observe o resultado.

O teste deverá apresentar uma falha.

Agora responda:

**1.** O que mudou no comportamento do teste?

**2.** Por que o teste falhou?

**3.** Qual era o resultado realmente produzido pela função?

**4.** Qual era o resultado esperado pelo teste?

**5.** Como o framework apresentou essa diferença?

**6.** O que essa experiência demonstra sobre a finalidade de um teste automatizado?

Depois, retorne o teste ao seu estado correto e confirme novamente a execução dos testes.

---

# 8. Parte 5 — Criando uma nova funcionalidade

Agora você deverá criar uma pequena funcionalidade no sistema.

Essa funcionalidade **não precisa representar uma regra real do sistema**.

O objetivo é criar uma função simples que permita exercitar o processo de criação de testes.

Você poderá, por exemplo, criar uma função:

```text
calcularDesconto()
```

que receba um valor e uma porcentagem de desconto e devolva o valor final.

Outro exemplo:

```text
calcularMedia()
```

que receba algumas notas e devolva a média.

Ou:

```text
verificarMaioridade()
```

que receba uma idade e informe se a pessoa é maior de idade.

Você poderá escolher outra função, desde que ela:

- receba dados;
- execute alguma regra;
- produza um resultado;
- possa ser testada automaticamente.

---

# 9. Parte 6 — Definindo o comportamento esperado

Antes de escrever o teste, descreva qual comportamento sua função deverá apresentar.

Por exemplo:

### Função

`calcularDesconto(100, 10)`

### Entrada

- valor: 100
- desconto: 10%

### Resultado esperado

90

O importante nesta etapa é definir claramente:

**Entrada → Regra → Resultado esperado**

Faça isso antes de criar os testes.

---

# 10. Parte 7 — Criando o teste de sucesso

Crie um teste automatizado para sua nova função.

O teste deverá:

1. fornecer os dados de entrada;
2. executar a função;
3. definir qual resultado é esperado;
4. comparar o resultado obtido com o resultado esperado;
5. ser aprovado quando a função estiver funcionando corretamente.

### Você deverá explicar:

- por que escolheu esses dados;
- qual resultado esperava;
- por que esse resultado representa o comportamento correto da função.

---

# 11. Parte 8 — Criando um cenário de falha

Agora deverá ser demonstrado que seu teste realmente é capaz de identificar um comportamento incorreto.

Para isso, provoque temporariamente uma situação de falha.

Você poderá fazer isso de duas maneiras:

### Opção A — Alterar temporariamente a implementação

Modifique propositalmente a função para produzir um resultado incorreto.

Execute o teste e observe a falha.

### Opção B — Alterar temporariamente o resultado esperado

Mantenha a função correta, mas faça o teste esperar um resultado incorreto.

Execute o teste e observe a falha.

Depois da demonstração, **restaure o código para que todos os testes voltem a passar**.

---

# 12. Parte 9 — Analisando a falha

Com o teste apresentando uma falha, responda:

**1.** Qual resultado o teste esperava?

**2.** Qual resultado a função produziu?

**3.** Por que os resultados são diferentes?

**4.** Em qual ponto o comportamento incorreto foi identificado?

**5.** Como você utilizaria a mensagem apresentada pelo framework para localizar o problema?

**6.** Por que essa identificação automática de problemas pode ser importante em um projeto maior?

---

# 13. Parte 10 — Reflexão final

Responda com suas próprias palavras:

**1.** Qual é a principal finalidade de um teste automatizado?

**2.** Qual a diferença entre testar manualmente uma função e possuir um teste automatizado para ela?

**3.** Por que um teste precisa possuir um resultado esperado?

**4.** O que significa dizer que um teste passou?

**5.** O que significa dizer que um teste falhou?

**6.** Por que provocar uma falha durante o desenvolvimento pode ser útil para compreender um teste?

**7.** Se uma função do sistema for alterada no futuro, como os testes existentes podem ajudar o programador?

**8.** Na sua opinião, testes automatizados servem apenas para encontrar erros? Justifique.

---

# 14. Entrega

A entrega deverá conter:

### A. Análise da estrutura

Explicação sobre como os testes existentes estão organizados.

### B. Análise dos testes existentes

Identificação do objetivo de cada teste já implementado.

### C. Execução

Registro dos resultados obtidos durante a execução dos testes.

### D. Simulação de falha

Demonstração de um teste funcionando e posteriormente apresentando uma falha provocada propositalmente.

### E. Nova funcionalidade

Código da nova função criada.

### F. Teste da nova funcionalidade

Teste automatizado criado pelo aluno.

### G. Análise

Explicação do funcionamento do teste e dos resultados obtidos.

### H. Reflexão final

Respostas às questões propostas na atividade.

---

# 15. Critérios de avaliação

| Critério | Valor |
|---|---:|
| Compreensão da estrutura dos testes existentes | 2,0 |
| Identificação e justificativa dos testes existentes | 2,0 |
| Execução e interpretação dos resultados | 1,5 |
| Criação da nova funcionalidade | 1,0 |
| Criação do teste automatizado | 1,5 |
| Demonstração e análise do cenário de falha | 1,0 |
| Clareza das explicações e reflexão final | 1,0 |
| **Total** | **10,0** |

---

# 16. Regra principal da atividade

**Não será avaliado apenas se o teste passa.**

O aluno deverá demonstrar que compreendeu:

> **O que está sendo testado → por que está sendo testado → qual resultado é esperado → como verificar o resultado → como identificar uma falha.**

Um teste que passa sem que o aluno consiga explicar o seu propósito **não demonstra compreensão suficiente da atividade**.

---

# 17. Desafio adicional — Para quem terminar antes

Crie um segundo teste para a sua função utilizando uma situação diferente.

Por exemplo:

- valor diferente;
- entrada diferente;
- limite da regra;
- valor mínimo;
- valor máximo;
- situação que possa produzir um resultado diferente.

Depois explique:

**Por que esse segundo teste é importante se o primeiro já passou?**

O objetivo é começar a perceber que **um único teste não necessariamente garante que uma função esteja correta em todas as situações.**