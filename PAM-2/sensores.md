# APOSTILA DE ESTUDO
# Sensores de Movimento e Orientação em Smartphones

**Disciplina:** Programação Mobile 2  
**Tema:** Física, Matemática e Lógica de Programação aplicadas a sensores  
**Tecnologia utilizada nas aulas práticas:** React Native + Expo

---

## 1. Introdução: como um celular consegue perceber o mundo físico?

Você já parou para pensar em como um celular consegue saber que está sendo movimentado, que foi girado ou para qual direção ele está apontando?

Pense em algumas situações do cotidiano:

- Um jogo no qual você movimenta uma bolinha inclinando o celular.
- Um aplicativo de bússola que indica o norte.
- Um jogo de corrida no qual você gira o celular para controlar o veículo.
- Um aplicativo que muda a orientação da tela quando você vira o aparelho.

O celular não possui olhos para enxergar esses movimentos. Ele utiliza pequenos componentes eletrônicos chamados **sensores**.

Esses componentes detectam fenômenos físicos e os transformam em sinais que podem ser interpretados pelo sistema operacional e pelos aplicativos.

Para entender como isso funciona, precisamos conectar três áreas do conhecimento:

1. **Física:** explica o fenômeno que o sensor detecta.
2. **Matemática:** permite representar e interpretar as informações recebidas.
3. **Lógica de programação:** transforma os dados em decisões e comportamentos do aplicativo.

Observe o caminho completo:

**Fenômeno físico → Sensor → Dados numéricos → Cálculos → Lógica de programação → Resposta na tela.**

Vamos estudar como esse processo funciona.

---

## 2. Antes dos sensores: entendendo os eixos X, Y e Z

Para interpretar os dados dos sensores, primeiro precisamos entender como o celular representa as direções no espaço.

Imagine um celular apoiado sobre uma mesa. Para descrever sua posição e seus movimentos, utilizamos três eixos: X, Y e Z.

- **Eixo X:** representa uma direção lateral do aparelho.
- **Eixo Y:** representa uma direção perpendicular à primeira, geralmente ao longo do comprimento do aparelho.
- **Eixo Z:** representa a direção perpendicular à superfície da tela, apontando para fora ou para dentro do aparelho.

Essas direções dependem do sistema de coordenadas adotado pelo dispositivo.

Podemos imaginar o celular como um pequeno objeto situado em um espaço tridimensional.

### Por que existem três eixos?

Porque o mundo físico possui três dimensões espaciais. Um objeto pode se movimentar para os lados, para cima e para baixo, para frente e para trás.

Da mesma forma, ele pode girar em torno de cada um desses eixos.

É importante entender que **os eixos pertencem ao sistema de coordenadas do dispositivo**. Eles não significam permanentemente “esquerda”, “direita”, “cima” ou “baixo” em relação à sala. Quando você gira o celular, os eixos giram junto com ele.

Isso será importante quando construirmos aplicativos que respondem à inclinação e à rotação do aparelho.

---

## 3. O acelerômetro: como o celular percebe a aceleração?

O primeiro sensor que estudaremos é o **acelerômetro**.

Ele mede a aceleração nos três eixos do aparelho. Para entender isso, precisamos distinguir três conceitos: posição, velocidade e aceleração.

### 3.1 Posição, velocidade e aceleração

Imagine um carro percorrendo uma estrada.

**Posição** indica onde o carro está.

**Velocidade** indica quanto sua posição muda ao longo do tempo.

**Aceleração** indica quanto sua velocidade muda ao longo do tempo.

Por exemplo, suponha que um carro esteja parado e comece a acelerar.

| Momento | Velocidade |
|---|---:|
| Início | 0 km/h |
| Após algum tempo | 20 km/h |
| Mais tarde | 40 km/h |

A velocidade aumentou. Portanto, houve aceleração.

A aceleração também pode ocorrer quando um objeto diminui a velocidade ou muda a direção do movimento.

Na Física, a aceleração média é calculada por:

**a = (v₂ − v₁) / Δt**

Em que:

- `a` é a aceleração;
- `v₁` é a velocidade inicial;
- `v₂` é a velocidade final;
- `Δt` é o intervalo de tempo.

Imagine que a velocidade de um objeto passe de 2 m/s para 8 m/s em 3 segundos.

A aceleração média será:

a = (8 − 2) / 3

a = 6 / 3

**a = 2 m/s²**

Isso significa que, em média, a velocidade aumentou 2 metros por segundo a cada segundo.

### 3.2 Como isso se aplica ao celular?

O acelerômetro possui uma estrutura microscópica capaz de detectar forças relacionadas ao movimento. Em muitos sensores, uma pequena massa interna se desloca em relação à estrutura do componente, e circuitos eletrônicos transformam essa variação em um sinal mensurável.

O sistema do celular converte esse sinal em valores numéricos.

Quando utilizamos o acelerômetro do Expo, recebemos informações nos eixos X, Y e Z.

Por exemplo:

```text
X:  0.12
Y:  0.97
Z: -0.04
```

Esses valores representam as componentes da aceleração detectada pelo sensor, conforme a convenção utilizada pela biblioteca.

**Atenção:** no `Accelerometer` do `expo-sensors`, os valores normalmente são expressos em unidades de gravidade, representadas por `g`, e não diretamente em m/s².

Uma unidade `g` corresponde aproximadamente a 9,81 m/s².

Assim, um valor de módulo próximo de 1 em determinado eixo pode indicar que a gravidade está sendo percebida principalmente naquela direção.

### 3.3 Por que um celular parado apresenta valores?

Essa é uma das questões mais importantes para compreender o acelerômetro.

Você pode apoiar o celular sobre uma mesa, sem movimentá-lo, e ainda observar valores próximos de:

```text
X: 0.00
Y: 0.00
Z: 1.00
```

Os valores exatos dependem da orientação do aparelho e da convenção de sinais do sensor.

Por que isso acontece?

Porque o acelerômetro também responde aos efeitos associados à gravidade. Em uma situação de repouso, ele normalmente registra uma componente de magnitude próxima de 1 g no eixo alinhado com a vertical, enquanto as outras componentes ficam próximas de zero.

Por isso, **acelerômetro não significa simplesmente detector de movimento**.

Ele também permite obter informações sobre a inclinação do aparelho em situações adequadas, mas seus dados precisam ser interpretados corretamente.

### 3.4 Experimento mental

Imagine três situações:

**Situação A:** o celular está apoiado sobre uma mesa, com a tela voltada para cima.

**Situação B:** você levanta o celular e o mantém parado, com uma lateral voltada para baixo.

**Situação C:** você movimenta o celular rapidamente.

Na situação A, a gravidade será percebida principalmente em um dos eixos do aparelho.

Na situação B, a componente da gravidade mudará de eixo porque o celular mudou de orientação.

Na situação C, além da gravidade, o sensor poderá registrar os efeitos da aceleração causada pelo movimento.

Essa diferença explica por que não podemos interpretar cada leitura isoladamente sem considerar o contexto físico.

---

## 4. O giroscópio: como o celular percebe uma rotação?

Agora vamos estudar o segundo sensor: o **giroscópio**.

Enquanto o acelerômetro mede aceleração, o giroscópio mede a velocidade angular, isto é, a rapidez com que o aparelho gira em torno de seus eixos.

Imagine que você mantenha o celular na mesma posição e comece a girá-lo sobre a mesa.

O giroscópio detecta essa rotação.

### 4.1 O que é velocidade angular?

Na Física, a velocidade angular indica quanto o ângulo de um objeto muda ao longo do tempo.

Ela pode ser calculada por:

**ω = Δθ / Δt**

Em que:

- `ω` representa a velocidade angular média;
- `Δθ` representa a variação do ângulo;
- `Δt` representa o intervalo de tempo.

Imagine que um objeto gire 90 graus em 3 segundos.

Sua velocidade angular média será:

ω = 90° / 3 s

ω = 30°/s

Isso significa que o objeto girou, em média, 30 graus por segundo.

Entretanto, os sensores de giroscópio frequentemente trabalham com ângulos em radianos.

### 4.2 O que são radianos?

Você provavelmente conhece os graus usados para medir ângulos.

Uma volta completa corresponde a 360 graus.

Na unidade radiano, essa mesma volta corresponde a 2π radianos.

Portanto:

- 180° = π radianos;
- 90° = π/2 radianos;
- 360° = 2π radianos.

A conversão de graus para radianos é:

**radianos = graus × π / 180**

E a conversão inversa é:

**graus = radianos × 180 / π**

Por exemplo, 90 graus correspondem a:

90 × π / 180 = π/2 ≈ 1,57 radianos.

Por que precisamos conhecer essa conversão?

Porque o giroscópio do `expo-sensors` fornece velocidades angulares normalmente em **radianos por segundo (rad/s)**, enquanto a propriedade `rotate` do React Native utiliza ângulos expressos em graus.

Precisamos, portanto, compreender as unidades antes de utilizar os valores.

### 4.3 Como transformar a velocidade angular em ângulo?

Imagine que o giroscópio informe uma velocidade angular constante de 1 rad/s durante 2 segundos.

A variação angular aproximada será:

**Δθ = ω × Δt**

Substituindo os valores:

Δθ = 1 × 2

Δθ = 2 radianos.

Convertendo para graus:

2 × 180 / π ≈ 114,6°.

Portanto, se a velocidade angular permanecer constante durante esses dois segundos, o objeto terá girado aproximadamente 114,6 graus.

Na prática, a velocidade muda continuamente. Por isso, o programa precisa considerar as leituras e os intervalos de tempo para estimar o ângulo acumulado.

Esse processo é chamado de **integração**.

Em uma implementação discreta, podemos usar a aproximação:

**Δθ ≈ ω × Δt**

E acumular as variações:

**θₙ = θₙ₋₁ + ωₙ × Δt**

Em que:

- `θₙ` é o ângulo estimado na leitura atual;
- `θₙ₋₁` é o ângulo estimado anteriormente;
- `ωₙ` é a velocidade angular atual;
- `Δt` é o tempo transcorrido desde a leitura anterior.

Observe que não basta somar os valores de velocidade angular. É necessário considerar quanto tempo passou entre as leituras.

### 4.4 Por que o cubo pode continuar girando ou apresentar erros?

Quando utilizamos apenas o giroscópio para estimar o ângulo, pequenos erros de medição podem se acumular.

Esse fenômeno é chamado de **drift**.

Imagine que cada leitura contenha um pequeno erro. Ao integrar milhares de leituras, esses erros podem fazer com que o ângulo calculado se afaste gradualmente do ângulo real.

Por isso, um aplicativo profissional pode combinar informações do giroscópio com as do acelerômetro e, em determinadas aplicações, do magnetômetro.

A combinação ajuda a corrigir limitações que cada sensor possui individualmente.

---

## 5. Acelerômetro e giroscópio: qual é a diferença?

Agora que conhecemos os dois sensores, vamos compará-los.

| Característica | Acelerômetro | Giroscópio |
|---|---|---|
| Grandeza medida | Aceleração | Velocidade angular |
| O que informa | Como a velocidade muda | Como a rotação muda ao longo do tempo |
| Unidade típica no Expo | `g` | `rad/s` |
| Pode ajudar a identificar inclinação? | Sim, em condições adequadas | Pode acompanhar mudanças de orientação, mas acumula erros |
| Exemplo de aplicação | Detectar inclinação de uma bolinha virtual | Estimar a rotação de um objeto virtual |

É importante não confundir aceleração com velocidade angular.

Imagine que você gire o celular e depois o mantenha parado em uma nova orientação.

O giroscópio tende a registrar velocidade angular próxima de zero quando a rotação termina, mesmo que o aparelho permaneça inclinado.

O acelerômetro, por sua vez, poderá continuar apresentando componentes da gravidade de acordo com a nova orientação.

Esse é um excelente experimento para observar a diferença entre os sensores.

---

## 6. O magnetômetro: como o celular identifica direções?

O terceiro sensor é o **magnetômetro**.

Ele mede o campo magnético ao redor do aparelho.

A Terra possui um campo magnético que permite a construção de bússolas. O magnetômetro de um smartphone pode detectar componentes desse campo e contribuir para determinar a direção em que o aparelho está apontando.

### 6.1 Como funciona uma bússola digital?

Uma bússola tradicional utiliza uma agulha magnetizada que tende a se alinhar ao campo magnético local.

No smartphone, o magnetômetro faz uma medição eletrônica desse campo.

Ele fornece componentes do campo magnético em diferentes eixos, normalmente representadas por:

```text
X: componente do campo magnético
Y: componente do campo magnético
Z: componente do campo magnético
```

Esses valores podem ser utilizados em cálculos para estimar a direção do campo.

Entretanto, receber X, Y e Z não significa que já temos uma bússola pronta.

Para calcular uma direção útil, o aplicativo precisa considerar a orientação do aparelho. Quando o celular está inclinado, por exemplo, é necessário compensar essa inclinação para obter uma direção horizontal confiável.

Também podem existir interferências magnéticas provocadas por objetos metálicos, ímãs, alto-falantes e outros equipamentos eletrônicos.

Por isso, algumas bússolas digitais precisam de calibração.

### 6.2 Magnetômetro não é GPS

É importante diferenciar esses componentes.

O GPS utiliza sinais de satélites para ajudar a estimar a localização geográfica do dispositivo.

O magnetômetro mede o campo magnético local.

Um aplicativo pode utilizar o GPS para saber onde o usuário está e o magnetômetro, combinado com outros sensores, para estimar para qual direção o aparelho está apontando.

São funções diferentes.

---

## 7. Como a matemática transforma os dados em informações úteis?

Até aqui, vimos que os sensores produzem números. Mas números, sozinhos, não executam uma tarefa.

O programa precisa interpretar esses valores.

Vamos imaginar que estamos construindo um aplicativo que detecta quando o celular está inclinado para a direita.

O sensor fornece um valor relacionado à inclinação. O programa pode comparar esse valor com um limite.

Por exemplo:

```js
if (dados.x > 0.5) {
  console.log('Inclinação detectada');
}
```

Esse código ilustra uma decisão baseada em um limite. Ele não constitui um detector universal de inclinação: o eixo, o sinal e o limite precisam ser verificados para a orientação física utilizada.

O raciocínio é:

1. Receber os dados do sensor.
2. Selecionar a informação relevante.
3. Comparar o valor com uma condição.
4. Executar uma ação quando a condição for satisfeita.

Esse processo utiliza conceitos fundamentais de programação.

### 7.1 Limites e condições

Suponha que queiramos identificar uma inclinação significativa.

Podemos definir um limite de referência:

```text
Se X > 0,5:
    indicar uma condição

Caso contrário:
    indicar outra condição
```

O valor 0,5 é apenas um exemplo. Ele não é um limite físico universal e precisa ser testado no dispositivo e na orientação escolhidos.

O mais importante é compreender que **o programa utiliza uma regra matemática para transformar uma leitura em uma decisão**.

### 7.2 Por que os valores variam mesmo quando o celular está parado?

Sensores reais não são perfeitos.

Eles podem apresentar pequenas variações causadas por ruído eletrônico, vibrações, resolução da medição e outros fatores.

Imagine as seguintes leituras:

```text
0,49
0,51
0,48
0,52
0,50
```

Se o programa considerar que o movimento foi detectado sempre que o valor ultrapassar 0,50, ele poderá alternar rapidamente entre dois estados.

Uma solução é utilizar uma faixa de tolerância ou um pequeno filtro.

Por exemplo, podemos definir que a condição de inclinação só será ativada acima de 0,55 e desativada quando o valor cair abaixo de 0,45.

Essa técnica cria uma diferença entre o limite de ativação e o de desativação, ajudando a evitar mudanças repetitivas quando os valores ficam próximos do limite.

Outra possibilidade é calcular uma média de várias leituras para reduzir oscilações. Contudo, a média também pode tornar a resposta mais lenta.

Assim, precisamos equilibrar estabilidade e rapidez.

---

## 8. Do sensor à interface: como isso funciona no React Native?

Agora vamos relacionar os conceitos físicos e matemáticos com o código que estamos desenvolvendo.

Nos nossos exemplos, utilizamos a biblioteca `expo-sensors`.

Quando escrevemos:

```js
import { Accelerometer } from 'expo-sensors';
```

estamos importando o componente da biblioteca que permite acessar as leituras do acelerômetro.

Para receber as medições continuamente, utilizamos:

```js
const subscription = Accelerometer.addListener((data) => {
  console.log(data);
});
```

A função recebe os dados disponibilizados pelo sensor.

O objeto `data` contém as componentes `x`, `y` e `z`.

Por exemplo:

```js
{
  x: 0.12,
  y: 0.97,
  z: -0.04
}
```

O método `addListener` permite registrar uma função que será executada quando novas medições forem disponibilizadas.

### 8.1 Por que utilizar o estado do React?

Na primeira etapa, mostramos os dados no console.

Na segunda etapa, queremos que os valores apareçam na tela.

Para isso, utilizamos o estado do React:

```js
const [dados, setDados] = useState({
  x: 0,
  y: 0,
  z: 0,
});
```

Quando recebemos uma nova leitura, fazemos:

```js
setDados(data);
```

O estado passa a armazenar os valores atuais.

A interface pode então apresentar:

```jsx
<Text>X: {dados.x.toFixed(2)}</Text>
<Text>Y: {dados.y.toFixed(2)}</Text>
<Text>Z: {dados.z.toFixed(2)}</Text>
```

O método `toFixed(2)` serve para apresentar duas casas decimais. Ele modifica a forma de exibição do número, não a medição física realizada pelo sensor.

O fluxo é:

**Sensor → `addListener()` → `setDados()` → renderização da interface.**

Quando o estado muda, o React atualiza a interface para refletir os novos valores.

É importante também remover a inscrição quando o componente deixa de ser utilizado:

```js
return () => {
  subscription.remove();
};
```

Isso evita manter uma inscrição desnecessária ativa.

---

## 9. Como controlar uma bolinha ou um cubo?

Agora podemos juntar Física, Matemática e Programação em uma aplicação concreta.

### 9.1 Controlando uma bolinha com o acelerômetro

Imagine uma bolinha desenhada dentro de uma área retangular.

Queremos que ela se mova quando o usuário inclinar o celular.

Podemos construir a lógica assim:

1. Receber os dados do acelerômetro.
2. Interpretar as componentes relevantes.
3. Calcular como a posição da bolinha deve mudar.
4. Respeitar os limites da área.
5. Atualizar a posição exibida na tela.

Podemos representar a posição da bolinha por duas variáveis:

```text
posiçãoX
posiçãoY
```

Se a posição horizontal aumentar, a bolinha se deslocará para um lado. Se diminuir, deslocará para o outro.

Entretanto, a relação entre o valor do sensor e a posição da bolinha precisa ser definida pelo programador. Podemos utilizar uma escala, uma velocidade de deslocamento e limites para impedir que a bolinha saia da área.

O acelerômetro não fornece diretamente a posição da bolinha. Ele fornece dados físicos que o programa transforma em deslocamento virtual.

### 9.2 Girando um cubo com o giroscópio

Para o cubo, o raciocínio é semelhante, mas a grandeza utilizada é diferente.

O giroscópio fornece a velocidade angular. O aplicativo utiliza essa velocidade e o tempo transcorrido para estimar a variação do ângulo.

A sequência é:

1. Receber a velocidade angular.
2. Calcular a variação angular durante o intervalo.
3. Acumular a variação no ângulo estimado.
4. Converter a unidade, se necessário.
5. Aplicar o ângulo à transformação visual do objeto.

Em um cubo 2D, podemos utilizar a propriedade `rotate` do React Native.

Em um objeto 3D real, precisamos representar rotações nos eixos e considerar a geometria e a orientação do objeto.

Essa diferença mostra que o sensor fornece informações físicas, enquanto o aplicativo define como essas informações serão representadas visualmente.

---

## 10. Limitações: por que os aplicativos precisam de mais matemática?

Você pode estar pensando: se os sensores já fornecem números, por que precisamos de tantos cálculos?

Porque cada sensor mede uma grandeza física específica e possui limitações.

O acelerômetro sofre influência da gravidade e não fornece diretamente a inclinação em todas as condições de movimento.

O giroscópio mede a velocidade angular, não o ângulo absoluto. Para estimar a orientação por integração, precisamos considerar o tempo e lidar com o acúmulo de erros.

O magnetômetro mede o campo magnético, que pode sofrer interferências e precisa ser interpretado de acordo com a orientação do aparelho.

Por isso, sistemas mais avançados podem combinar vários sensores.

Essa combinação é conhecida como **fusão de sensores**.

De maneira simplificada:

- O acelerômetro contribui com informações sobre aceleração e direção da gravidade em condições adequadas.
- O giroscópio ajuda a acompanhar mudanças rápidas de rotação.
- O magnetômetro contribui para estimar a direção em relação ao campo magnético terrestre.

Combinando essas informações, um sistema pode produzir estimativas de orientação mais estáveis do que utilizando apenas um sensor.

Isso não elimina todas as limitações, mas permite aproveitar as vantagens de cada componente.

---

## 11. Resumo: o que você precisa compreender

Antes de avançar para os próximos exercícios, certifique-se de compreender estas ideias:

**Acelerômetro:** mede aceleração nos eixos do dispositivo. A gravidade influencia suas leituras, inclusive quando o celular está em repouso.

**Giroscópio:** mede velocidade angular. Para estimar a variação do ângulo ao longo do tempo, precisamos considerar a velocidade angular e o intervalo entre as medições.

**Magnetômetro:** mede o campo magnético. Seus dados podem contribuir para determinar direções, mas uma bússola confiável exige interpretação adequada e pode precisar de calibração.

**Matemática:** permite converter unidades, calcular variações, comparar valores, estimar ângulos e interpretar as leituras.

**Lógica de programação:** permite estabelecer condições, aplicar regras, atualizar estados e transformar medições em comportamentos do aplicativo.

**React Native:** recebe os dados por meio da biblioteca, mantém o estado atualizado e representa os resultados na interface.

A ideia fundamental é esta:

**O sensor mede. A matemática interpreta. A lógica decide. O aplicativo reage.**

---

## 12. Atividade de fixação

Responda às questões utilizando suas próprias palavras. O objetivo não é apenas decorar definições, mas demonstrar que você compreendeu os conceitos.

### Parte A — Compreensão conceitual

**1.** Qual é a diferença entre posição, velocidade e aceleração? Apresente um exemplo cotidiano.

**2.** Por que um acelerômetro pode apresentar valores diferentes de zero mesmo quando o celular está apoiado e aparentemente parado?

**3.** Qual é a principal diferença entre o acelerômetro e o giroscópio?

**4.** O giroscópio informa diretamente o ângulo absoluto do celular? Explique.

**5.** Qual é a função do magnetômetro e por que ele não deve ser confundido com o GPS?

### Parte B — Matemática aplicada

**6.** Um objeto aumenta sua velocidade de 4 m/s para 10 m/s em 3 segundos. Calcule sua aceleração média.

**7.** Um objeto gira 120 graus em 4 segundos, com velocidade angular média constante. Qual é essa velocidade em graus por segundo?

**8.** Converta 180 graus para radianos.

**9.** Um giroscópio registra velocidade angular constante de 0,5 rad/s durante 2 segundos. Qual é a variação angular aproximada em radianos? E em graus?

**10.** Por que é necessário considerar o intervalo de tempo ao acumular as leituras do giroscópio?

### Parte C — Lógica de programação

**11.** Um programa recebe um valor do sensor e verifica se ele é maior que 0,5. Qual estrutura de programação pode ser utilizada para tomar uma decisão com base nessa condição?

**12.** Por que um aplicativo pode apresentar comportamentos instáveis quando os valores do sensor ficam oscilando próximos de um limite?

**13.** Qual é a função do `useState` no exemplo que mostra X, Y e Z na tela?

**14.** Explique o caminho percorrido pelos dados desde a leitura do sensor até a atualização da interface.

**15.** Em um jogo de bolinha controlada pela inclinação do celular, o acelerômetro fornece diretamente a posição da bolinha? Explique o papel da lógica de programação.

### Parte D — Desafio de análise

**16.** Imagine que você girou o celular e depois o manteve parado em uma nova orientação. O que você espera observar no giroscópio durante a rotação e depois que ela termina?

**17.** Um aluno afirma: “Se eu somar todos os valores do giroscópio, terei o ângulo correto do celular”. Explique por que essa afirmação está incompleta.

**18.** Um aplicativo de bússola apresenta uma direção instável quando o celular está perto de um objeto metálico. Qual sensor pode estar sendo afetado e por quê?

**19.** Você precisa construir um aplicativo que mostre os valores de um sensor no console e, posteriormente, na tela. Quais são as etapas de desenvolvimento que você seguiria?

**20.** Escolha uma aplicação de smartphone que utilize sensores de movimento ou orientação. Explique quais sensores podem participar, quais dados são obtidos e como a programação pode transformá-los em uma funcionalidade útil.

---

## Conclusão

Ao desenvolver aplicativos com sensores, você não está apenas aprendendo a utilizar uma biblioteca de programação. Está aprendendo a transformar fenômenos físicos em informações digitais.

Esse conhecimento é importante para o desenvolvimento de jogos, aplicativos de navegação, interfaces interativas, dispositivos vestíveis, robótica e sistemas que precisam perceber mudanças no ambiente.

Nas próximas aulas práticas, utilizaremos esses conceitos para construir aplicativos progressivamente: primeiro observaremos as leituras, depois interpretaremos os dados e, por fim, utilizaremos os sensores para controlar objetos na tela.

O objetivo é que você consiga explicar não apenas **como fazer funcionar**, mas também **por que funciona**.
