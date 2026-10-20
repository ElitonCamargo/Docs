# Lista de Exercícios Investigativos
## Física, Matemática e Lógica aplicadas aos sensores de smartphones

**Disciplina:** Programação Mobile 2  
**Tecnologia utilizada:** React Native + Expo  
**Tema:** Interpretação de dados de sensores

---

## Orientações gerais

A proposta desta atividade é investigar como a **Física**, a **Matemática** e a **Lógica de Programação** são utilizadas para interpretar os dados produzidos pelos sensores de um smartphone.

As respostas devem apresentar raciocínio, cálculos, hipóteses, testes e conclusões. Respostas sem justificativa não serão consideradas completas.

Sempre que possível, registre valores coletados no próprio dispositivo e compare aquilo que você esperava observar com o que realmente aconteceu.

> **Importante:** o objetivo não é apenas chegar a uma resposta, mas explicar como ela foi construída.

---

## Exercício 1 — Previsão dos eixos do acelerômetro

Antes de abrir qualquer aplicativo de sensores, coloque o celular sobre uma mesa, com a tela voltada para cima.

### Etapas

1. Desenhe um celular e indique como você imagina que estejam orientados os eixos X, Y e Z.
2. Preveja qual eixo apresentará o maior valor absoluto.
3. Preveja se esse valor será positivo ou negativo.
4. Em seguida, execute um aplicativo que mostre os valores do acelerômetro.
5. Registre cinco leituras diferentes.

Utilize o seguinte formato:

```text
Leitura 1: X = ____  Y = ____  Z = ____
Leitura 2: X = ____  Y = ____  Z = ____
Leitura 3: X = ____  Y = ____  Z = ____
Leitura 4: X = ____  Y = ____  Z = ____
Leitura 5: X = ____  Y = ____  Z = ____
```

### Análise

Responda:

- Sua previsão estava correta?
- Qual eixo apresentou o maior valor absoluto?
- Por que os outros eixos não permaneceram exatamente em zero?
- O que aconteceria com os valores se o celular fosse colocado com a tela voltada para baixo?

**Importante:** não basta informar os valores. Relacione as observações com a gravidade e com o sistema de coordenadas do aparelho.

---

## Exercício 2 — Movimento ou mudança de orientação?

Considere duas experiências:

- **Experiência A:** o celular é deslocado rapidamente para a direita e depois retorna à posição inicial.
- **Experiência B:** o celular é lentamente inclinado para a direita e permanece parado nessa nova orientação.

Sem realizar o experimento, formule uma hipótese sobre o comportamento do acelerômetro em cada situação.

Depois, realize os dois movimentos e observe as leituras.

### Produção solicitada

Para cada experiência, explique:

1. Quais eixos sofreram as maiores alterações?
2. As alterações foram momentâneas ou permaneceram?
3. Em qual experiência a gravidade teve maior importância na leitura?
4. É possível determinar, analisando uma única leitura, se o celular está em movimento ou somente inclinado? Justifique.

Ao final, escreva uma regra explicando por que a frase abaixo pode estar incorreta:

> “Se o acelerômetro mostrar um valor diferente de zero, o celular está se movimentando.”

---

## Exercício 3 — Aceleração e unidade `g`

Durante um experimento, um aplicativo apresentou as seguintes leituras do acelerômetro:

```text
X = 0,30 g
Y = 0,40 g
Z = 0,80 g
```

Considere:

```text
1 g ≈ 9,81 m/s²
```

### Tarefas

1. Converta cada componente para `m/s²`.
2. Calcule o módulo aproximado da aceleração resultante utilizando:

```text
|a| = √(X² + Y² + Z²)
```

3. Realize o cálculo primeiro utilizando os valores em `g`.
4. Converta o resultado final para `m/s²`.
5. Compare o resultado com `1 g`.

### Análise

Explique:

- O resultado indica que a gravidade pode estar influenciando a leitura?
- É correto afirmar que o aparelho está acelerando em três movimentos independentes?
- Por que analisar somente um eixo pode produzir uma interpretação incompleta?

Todos os cálculos devem ser apresentados. Uma resposta contendo apenas o resultado final não será considerada completa.

---

## Exercício 4 — Construção de uma regra de decisão

Um aplicativo precisa apresentar uma destas mensagens:

- `Inclinado para um lado`
- `Posição aproximadamente central`
- `Inclinado para o outro lado`

Durante os testes, foram obtidos os seguintes valores em um dos eixos:

```text
-0,72
-0,48
-0,12
 0,03
 0,19
 0,51
 0,76
```

Você deverá construir uma regra de decisão, mas não poderá simplesmente utilizar:

```text
Se X > 0:
    indicar um lado
Caso contrário:
    indicar o outro lado
```

### Tarefas

1. Escolha dois limites numéricos para separar as três condições.
2. Escreva sua regra em pseudocódigo.
3. Classifique cada um dos sete valores apresentados.
4. Justifique por que escolheu esses limites.
5. Explique o que poderia acontecer se o limite central fosse muito pequeno.
6. Explique o que poderia acontecer se o limite central fosse muito grande.

Não existe uma única escolha correta de limites. A qualidade da resposta dependerá da justificativa e da coerência da regra.

---

## Exercício 5 — O problema da oscilação próxima ao limite

Um aplicativo ativa um alerta quando o valor de X é maior que `0,50`.

O sensor produziu a sequência:

```text
0,47
0,49
0,51
0,52
0,50
0,48
0,51
0,49
0,53
0,47
```

### Tarefas

1. Indique, para cada leitura, se o alerta estaria ligado ou desligado.
2. Conte quantas mudanças de estado ocorreriam.
3. Explique por que esse comportamento pode ser inadequado para o usuário.
4. Crie uma nova regra com:
   - um limite para ligar o alerta;
   - outro limite para desligá-lo.
5. Aplique sua nova regra à mesma sequência.
6. Compare a quantidade de mudanças produzida pelas duas soluções.

Exemplo do tipo de raciocínio esperado:

```text
Se o alerta estiver desligado, ele somente será ligado quando...
Se o alerta estiver ligado, ele somente será desligado quando...
```

Explique por que a nova solução é mais estável e identifique uma possível desvantagem dela.

---

## Exercício 6 — Do giroscópio ao ângulo estimado

Um giroscópio registrou a velocidade angular em torno do eixo Z durante cinco intervalos de tempo:

```text
Intervalo 1: ω = 0,40 rad/s e Δt = 0,20 s
Intervalo 2: ω = 0,80 rad/s e Δt = 0,10 s
Intervalo 3: ω = 1,20 rad/s e Δt = 0,15 s
Intervalo 4: ω = 0,50 rad/s e Δt = 0,30 s
Intervalo 5: ω = -0,30 rad/s e Δt = 0,20 s
```

Utilize:

```text
Δθ = ω × Δt
```

### Tarefas

1. Calcule a variação angular de cada intervalo.
2. Indique em qual intervalo ocorreu a maior variação angular.
3. Calcule o ângulo acumulado ao final dos cinco intervalos.
4. Converta o resultado para graus:

```text
graus = radianos × 180 / π
```

5. Explique o significado do valor negativo no último intervalo.

### Reflexão

Um aluno afirmou:

> “O intervalo 3 produziu a maior variação porque apresentou a maior velocidade angular.”

Determine se a conclusão está correta, mas analise também se o raciocínio utilizado pelo aluno é suficiente.

---

## Exercício 7 — Investigação do *drift* do giroscópio

Coloque o celular parado sobre uma superfície estável e registre os valores do giroscópio durante pelo menos 20 segundos.

### Antes do experimento

Responda:

- Quais valores você espera obter?
- Você acredita que obterá exatamente zero em todos os eixos?
- Se valores pequenos forem acumulados durante vários minutos, o que poderá acontecer com o ângulo estimado?

### Depois do experimento

1. Registre pelo menos dez leituras.
2. Escolha um dos eixos.
3. Considere um intervalo constante entre as leituras.
4. Estime a variação angular produzida pelas pequenas velocidades registradas.
5. Explique como um celular parado pode gerar uma rotação virtual acumulada.

### Proposta de solução

Apresente uma estratégia para reduzir esse problema. Sua estratégia pode envolver:

- uma zona de tolerância;
- correção com outro sensor;
- calibração inicial;
- média de leituras;
- redefinição periódica do ângulo.

Você deverá explicar também uma possível desvantagem da estratégia escolhida.

---

## Exercício 8 — Diagnóstico de uma bússola instável

Um aplicativo de bússola apresenta os seguintes comportamentos:

- funciona normalmente no centro da sala;
- muda de direção quando se aproxima de uma caixa de som;
- apresenta valores diferentes quando é colocado próximo a uma estrutura metálica;
- fica instável quando o aparelho está muito inclinado.

### Tarefas

Produza um diagnóstico respondendo:

1. Qual sensor está diretamente relacionado aos dois primeiros problemas?
2. Por que uma caixa de som pode interferir nas leituras?
3. Por que objetos metálicos podem alterar o resultado?
4. Por que a inclinação do aparelho dificulta a obtenção de uma direção horizontal?
5. Quais outros sensores poderiam contribuir para corrigir ou compensar a orientação?
6. Por que o GPS, sozinho, não resolve completamente o problema?

Ao final, elabore um procedimento de teste que permita diferenciar:

- erro causado por interferência magnética;
- erro causado pela inclinação do aparelho;
- erro produzido pela lógica do programa.

O procedimento deve apresentar uma sequência clara de testes, e não apenas uma explicação teórica.

---

## Exercício 9 — Auditoria de uma lógica de controle

Um programador criou a seguinte lógica para movimentar uma bolinha:

```text
Se X > 0,5:
    aumentar posiçãoX em 10
Caso contrário:
    diminuir posiçãoX em 10
```

### Análise crítica

Identifique pelo menos **quatro problemas** nessa solução.

Considere situações como:

- celular aproximadamente central;
- valores próximos de zero;
- atualização muito rápida do sensor;
- limites da tela;
- aparelhos com diferentes taxas de atualização;
- orientação do dispositivo;
- pequenas oscilações nas leituras.

Depois, escreva um pseudocódigo melhorado que considere:

1. uma zona central;
2. movimentos nos dois sentidos;
3. intensidade da inclinação;
4. limites da área disponível;
5. intervalo de tempo entre as atualizações.

### Justificativa obrigatória

Explique como cada melhoria modifica o comportamento da bolinha.

Não será suficiente apresentar um código pronto. O principal objetivo é demonstrar quais problemas foram identificados e como as decisões de programação tentam resolvê-los.

---

## Exercício 10 — Projeto investigativo: do fenômeno físico à resposta do aplicativo

Escolha uma das propostas:

- jogo de equilíbrio;
- contador de movimentos;
- nível digital;
- bússola;
- controle de um veículo virtual;
- rotação de um objeto;
- detector de mudança de orientação;
- outra aplicação aprovada pelo professor.

### Parte 1 — Planejamento

Antes de programar, produza um documento contendo:

1. O fenômeno físico que será observado.
2. O sensor ou conjunto de sensores utilizado.
3. A grandeza física medida por cada sensor.
4. As unidades envolvidas.
5. Os eixos utilizados.
6. As condições e os cálculos necessários.
7. Os valores de referência inicialmente escolhidos.
8. Os comportamentos esperados na interface.
9. As possíveis fontes de erro.
10. Uma hipótese sobre o funcionamento do aplicativo.

### Parte 2 — Experimento

Construa uma versão simples do aplicativo e realize pelo menos três testes em condições diferentes.

Para cada teste, registre:

```text
Condição física:
Valores observados:
Resposta esperada:
Resposta produzida:
Diferenças encontradas:
Possível explicação:
Alteração realizada no programa:
```

### Parte 3 — Defesa da solução

Apresente uma explicação utilizando obrigatoriamente a sequência:

```text
Fenômeno físico
        ↓
Medição do sensor
        ↓
Dados numéricos
        ↓
Cálculo ou tratamento
        ↓
Decisão lógica
        ↓
Resposta do aplicativo
```

Finalize respondendo:

- Qual foi a decisão de programação mais difícil?
- Qual comportamento observado contrariou sua hipótese inicial?
- Que alteração melhorou mais o aplicativo?
- O que ainda não foi resolvido?
- Como você demonstraria que sua solução funciona e não apresenta apenas resultados ocasionais?

---

# Regras para entrega

Para que a atividade exija investigação e autoria, cada aluno ou grupo deverá entregar:

- hipóteses registradas **antes** dos experimentos;
- valores coletados no próprio aparelho;
- cálculos com as etapas apresentadas;
- justificativas para os limites escolhidos;
- comparação entre resultado esperado e resultado observado;
- evidências dos testes, como capturas de tela, tabelas ou pequenos vídeos;
- conclusão escrita com as próprias palavras;
- identificação do modelo do aparelho utilizado;
- indicação das limitações encontradas.

Quando houver programação, o estudante deverá ser capaz de explicar oralmente:

- o significado das variáveis;
- a origem dos valores numéricos;
- as condições utilizadas;
- a relação entre os dados físicos e a resposta visual;
- o que aconteceria se determinados valores fossem modificados.

## Critério central de avaliação

> A resposta não será avaliada apenas por estar correta. Será avaliada pela capacidade do estudante de **prever, testar, calcular, interpretar, justificar e revisar suas conclusões**.
