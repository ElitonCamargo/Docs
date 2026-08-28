# React Native — Estado e Eventos de Toque

## 1. Introdução

Até aqui, aprendemos a criar componentes React Native e utilizar `props` para passar informações entre eles.

Nesta etapa, vamos aprender dois conceitos fundamentais para criar aplicativos **interativos**:

* **Estado (`state`)**
* **Eventos de toque (`onPress`)**

Esses dois conceitos trabalham juntos para permitir que o aplicativo **reaja às ações do usuário**.

Como exemplo, vamos criar um aplicativo que sorteia um número entre **1 e 100** sempre que o usuário tocar em um botão.

---

## 2. O que vamos aprender

Ao final deste conteúdo, você deverá compreender:

* O que é uma variável de estado;
* O que são Hooks;
* Como utilizar o Hook `useState`;
* Como alterar o estado de um componente;
* O que é o evento `onPress`;
* Como executar uma função quando um botão é pressionado;
* Como uma alteração de estado provoca uma nova renderização da interface;
* Como gerar números aleatórios em JavaScript;
* Como combinar estado e eventos para criar uma interface interativa.

---

# 3. O que é estado?

Em uma aplicação, existem informações que podem mudar durante sua execução.

Por exemplo:

* nome de um usuário;
* quantidade de produtos em um carrinho;
* situação de um botão;
* texto digitado em um campo;
* número sorteado em um jogo;
* contador de pontos.

Essas informações podem ser chamadas de **estado** da aplicação ou de um componente.

No React Native, utilizamos o **State** para armazenar informações que podem mudar e que precisam ser refletidas na interface.

### Exemplo

Imagine que temos inicialmente:

```text
Número: 0
```

O usuário toca no botão:

```text
Sortear
```

O aplicativo gera:

```text
Número: 73
```

O valor mudou.

Precisamos então de uma forma de informar ao React Native:

> "O valor mudou. Atualize a interface."

É exatamente nesse cenário que utilizamos o `useState`.

---

# 4. O Hook `useState`

O React fornece recursos chamados **Hooks**.

Hooks são funções especiais que permitem utilizar determinados recursos do React dentro de componentes funcionais.

Um dos Hooks mais utilizados é:

```javascript
useState
```

Ele permite criar e controlar uma variável de estado.

Para utilizá-lo, fazemos a importação:

```javascript
import React, { useState } from 'react';
```

Depois podemos criar um estado:

```javascript
const [numero, setNumero] = useState(0);
```

Nesse exemplo temos:

```text
numero
   ↓
valor atual do estado

setNumero
   ↓
função utilizada para alterar o estado

useState(0)
   ↓
valor inicial do estado
```

---

# 5. Entendendo o `useState`

Observe:

```javascript
const [numero, setNumero] = useState(0);
```

Podemos interpretar essa instrução da seguinte maneira:

```text
┌─────────────────────────────────────┐
│             useState(0)             │
│                                     │
│        Estado inicial = 0           │
└──────────────────┬──────────────────┘
                   │
                   ▼
          ┌─────────────────┐
          │      numero     │
          │   valor atual   │
          └─────────────────┘
                   │
                   │ alteração
                   ▼
          ┌─────────────────┐
          │    setNumero    │
          │ função que muda │
          │     o estado    │
          └─────────────────┘
```

O primeiro elemento representa o **valor atual**.

O segundo representa a **função utilizada para atualizar esse valor**.

Por convenção, usamos nomes como:

```javascript
const [nome, setNome] = useState('');
const [idade, setIdade] = useState(0);
const [contador, setContador] = useState(0);
```

O padrão normalmente é:

```text
[valor, setValor]
```

---

# 6. Por que não utilizar uma variável comum?

Poderíamos pensar em fazer:

```javascript
let numero = 0;
```

E depois:

```javascript
numero = 50;
```

Mas isso não é suficiente para controlar uma informação que precisa ser exibida na interface.

Quando o valor utilizado pela interface muda, precisamos que o React saiba que deve **renderizar novamente o componente**.

Por isso utilizamos:

```javascript
const [numero, setNumero] = useState(0);
```

Quando fazemos:

```javascript
setNumero(50);
```

o React é informado de que o estado mudou.

Como consequência, o componente é renderizado novamente utilizando o novo valor.

---

# 7. Estado e renderização

Considere o seguinte componente:

```javascript
const Tela = () => {
  const [numero, setNumero] = useState(0);

  return (
    <Text>{numero}</Text>
  );
};
```

Inicialmente:

```text
numero = 0
```

A tela apresenta:

```text
0
```

Quando executamos:

```javascript
setNumero(50);
```

o estado passa a ser:

```text
numero = 50
```

O React renderiza o componente novamente.

A tela passa a apresentar:

```text
50
```

Podemos representar o processo assim:

```text
setNumero(50)
      ↓
estado é atualizado
      ↓
React identifica a alteração
      ↓
componente é renderizado novamente
      ↓
novo valor aparece na interface
```

Esse é um dos conceitos mais importantes desta aula.

---

# 8. Desestruturação de arrays

A criação do estado utiliza um recurso da linguagem JavaScript chamado **desestruturação**.

Por exemplo:

```javascript
const tecnologias = ['JavaScript', 'React'];

const [linguagem, frontend] = tecnologias;
```

Agora:

```javascript
linguagem
```

contém:

```text
JavaScript
```

E:

```javascript
frontend
```

contém:

```text
React
```

Isso acontece porque os valores do array são atribuídos às variáveis de acordo com sua posição.

```text
tecnologias
     │
     ├── posição 0 → JavaScript
     │
     └── posição 1 → React

        ↓ desestruturação

linguagem = JavaScript
frontend  = React
```

O `useState` utiliza esse mesmo conceito:

```javascript
const [numero, setNumero] = useState(0);
```

O `useState` retorna dois valores:

```text
valor atual
função de atualização
```

A desestruturação permite atribuir esses dois valores às variáveis:

```text
numero
setNumero
```

---

# 9. O que são Hooks?

Hooks são funções especiais disponibilizadas pelo React para permitir que componentes funcionais utilizem recursos do React.

Alguns exemplos conhecidos são:

```javascript
useState
useEffect
useContext
```

Nesta aula vamos trabalhar especificamente com:

```javascript
useState
```

Uma característica importante dos Hooks é que eles devem ser utilizados seguindo as regras definidas pelo React.

Por exemplo, o `useState` normalmente é declarado diretamente dentro do componente:

```javascript
const TelaInicial = () => {
  const [numero, setNumero] = useState(0);

  // ...
};
```

Não devemos criar o estado dentro de estruturas condicionais ou loops:

```javascript
// Evite fazer isso
if (condicao) {
  const [numero, setNumero] = useState(0);
}
```

Para esta etapa, o mais importante é compreender:

> `useState` permite que o componente mantenha um valor entre suas renderizações e seja atualizado quando esse valor mudar.

---

# 10. O que é um evento?

Um evento representa uma ação que acontece durante a utilização da aplicação.

Exemplos:

* tocar em um botão;
* pressionar uma área da tela;
* digitar em um campo;
* alterar um campo;
* selecionar uma opção.

Em uma aplicação mobile, uma das ações mais comuns é o **toque**.

No React Native, vários componentes oferecem propriedades para responder a interações do usuário.

Uma delas é:

```javascript
onPress
```

---

# 11. O evento `onPress`

O `onPress` permite definir uma função que será executada quando o usuário tocar em determinado componente que suporta esse evento.

Exemplo:

```javascript
<Button
  title="Clique aqui"
  onPress={minhaFuncao}
/>
```

Nesse caso, quando o usuário tocar no botão, a função:

```javascript
minhaFuncao
```

será executada.

Podemos representar:

```text
Usuário toca no botão
          ↓
       onPress
          ↓
   minhaFuncao()
          ↓
      ação executada
```

---

# 12. `onPress` e funções

Podemos criar uma função para executar uma determinada ação:

```javascript
const mostrarMensagem = () => {
  console.log('Botão pressionado');
};
```

Depois associamos essa função ao botão:

```javascript
<Button
  title="Clique aqui"
  onPress={mostrarMensagem}
/>
```

Quando o botão for pressionado:

```text
Usuário
   ↓
toca no botão
   ↓
onPress
   ↓
mostrarMensagem()
   ↓
"Botão pressionado"
```

---

# 13. Uma atenção importante com `onPress`

Observe:

```javascript
onPress={mostrarMensagem}
```

Estamos passando a **função**.

Não devemos, nesse caso, fazer:

```javascript
onPress={mostrarMensagem()}
```

A diferença é importante.

### Passando a função

```javascript
onPress={mostrarMensagem}
```

Significa:

> "Quando acontecer o evento, execute essa função."

### Executando imediatamente

```javascript
onPress={mostrarMensagem()}
```

Significa:

> "Execute essa função agora e utilize o resultado dela."

Portanto, quando queremos associar uma função diretamente ao `onPress`, utilizamos:

```javascript
onPress={mostrarMensagem}
```

---

# 14. Quais componentes possuem `onPress`?

Não podemos assumir que qualquer componente possui a propriedade `onPress`.

Alguns componentes que permitem interação por toque incluem:

* `Button`
* `Pressable`
* `TouchableOpacity`
* `TouchableHighlight`

Por exemplo:

```javascript
<Button
  title="Sortear"
  onPress={gerarNumero}
/>
```

O componente `Button` possui suporte ao `onPress`.

---

# 15. Criando o aplicativo de sorteio

Agora vamos juntar os dois conceitos principais:

```text
useState
+
onPress
```

Nosso objetivo será criar:

```text
┌─────────────────────────────┐
│       Sorteio DevMedia      │
│ Hora de ver quem é vencedor │
├─────────────────────────────┤
│                             │
│  Toque no botão e veja quem │
│  é o vencedor de 1 à 100    │
│                             │
│           ┌─────┐           │
│           │  73 │           │
│           └─────┘           │
│                             │
│         [ Sortear ]         │
│                             │
└─────────────────────────────┘
```

Quando o usuário tocar em **Sortear**, um novo número deverá aparecer.

---

# 16. Criando o estado `numeroSorteado`

Primeiro importamos o `useState`:

```javascript
import React, { useState } from 'react';
```

Depois criamos o estado:

```javascript
const [numeroSorteado, setNumeroSorteado] = useState(0);
```

Temos:

| Elemento            | Função                     |
| ------------------- | -------------------------- |
| `numeroSorteado`    | valor atual do número      |
| `setNumeroSorteado` | função que altera o estado |
| `0`                 | valor inicial              |

Podemos exibir o estado na tela:

```javascript
<Text>
  {numeroSorteado}
</Text>
```

Inicialmente teremos:

```text
0
```

---

# 17. Criando a função `gerarNumero`

Agora precisamos criar uma função que gere um número aleatório.

```javascript
const gerarNumero = () => {
  const novoNumero = Math.floor(Math.random() * (101 - 1) + 1);

  setNumeroSorteado(novoNumero);
};
```

Vamos analisar cada parte.

---

# 18. `Math.random()`

A função:

```javascript
Math.random()
```

gera um número aleatório maior ou igual a `0` e menor que `1`.

Exemplos possíveis:

```text
0.13
0.58
0.91
0.42
```

Ela nunca retorna exatamente `1`.

---

# 19. `Math.floor()`

A função:

```javascript
Math.floor()
```

arredonda um número para baixo, retornando o maior número inteiro menor ou igual ao valor informado.

Exemplo:

```javascript
Math.floor(4.8);
```

Resultado:

```text
4
```

Outro exemplo:

```javascript
Math.floor(9.99);
```

Resultado:

```text
9
```

---

# 20. Gerando um número entre 1 e 100

Utilizamos:

```javascript
Math.floor(Math.random() * (101 - 1) + 1);
```

Podemos simplificar matematicamente:

```javascript
Math.floor(Math.random() * 100 + 1);
```

O resultado será um número inteiro entre:

```text
1
```

e:

```text
100
```

inclusive.

A lógica é:

```text
Math.random()
      ↓
número entre 0 e menor que 1
      ↓
× 100
      ↓
número entre 0 e menor que 100
      ↓
+ 1
      ↓
número entre 1 e menor que 101
      ↓
Math.floor()
      ↓
inteiro entre 1 e 100
```

---

# 21. Atualizando o estado

Depois de gerar o número, precisamos atualizar o estado:

```javascript
setNumeroSorteado(novoNumero);
```

Por exemplo, se:

```javascript
novoNumero = 73;
```

teremos:

```javascript
setNumeroSorteado(73);
```

O estado será atualizado:

```text
numeroSorteado = 73
```

E o React Native poderá atualizar a interface.

---

# 22. Associando a função ao botão

Agora basta associar a função ao `onPress`:

```javascript
<Button
  title="Sortear"
  onPress={gerarNumero}
/>
```

O fluxo completo passa a ser:

```text
Usuário toca em "Sortear"
             ↓
          onPress
             ↓
        gerarNumero()
             ↓
        Math.random()
             ↓
        novoNumero
             ↓
   setNumeroSorteado()
             ↓
       estado alterado
             ↓
   componente renderizado
             ↓
    novo número exibido
```

Esse é o funcionamento central do nosso aplicativo.

---

# 23. Código completo do componente

O componente `TelaInicial` pode ficar assim:

```javascript
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';
import estilo from './estilo';

const TelaInicial = () => {
  const [numeroSorteado, setNumeroSorteado] = useState(0);

  const gerarNumero = () => {
    const novoNumero = Math.floor(Math.random() * 100 + 1);

    setNumeroSorteado(novoNumero);
  };

  return (
    <View style={estilo.tela}>

      <Text style={estilo.tituloTexto}>
        Toque no botão e veja quem é o vencedor de 1 à 100
      </Text>

      <View style={estilo.boxNumero}>
        <Text style={estilo.numero}>
          {numeroSorteado}
        </Text>
      </View>

      <View style={estilo.boxBotao}>
        <Button
          title="Sortear"
          onPress={gerarNumero}
          color="#1f4f66"
        />
      </View>

    </View>
  );
};

export default TelaInicial;
```

---

# 24. O código completo da aplicação

Uma versão simplificada da aplicação pode ser construída assim:

```javascript
import React, { useState } from 'react';
import { View, Text, Button, StyleSheet } from 'react-native';

const estilo = StyleSheet.create({
  boxTitulo: {
    height: 80,
    backgroundColor: '#1f4f66',
    paddingHorizontal: 10,
    paddingTop: 10,
    justifyContent: 'center',
  },

  tituloCabecalho: {
    color: '#0fc3d4',
    fontWeight: '700',
    fontSize: 20,
  },

  subtitulo: {
    color: '#fff',
  },

  tela: {
    width: '100%',
    justifyContent: 'center',
    alignItems: 'center',
  },

  boxNumero: {
    borderColor: '#13b0c5',
    backgroundColor: '#13b0c5',
    borderWidth: 5,
    height: 150,
    width: 150,
    borderRadius: 75,
    justifyContent: 'center',
    alignItems: 'center',
    marginBottom: 50,
  },

  tituloTexto: {
    fontSize: 14,
    marginVertical: 30,
    paddingHorizontal: 20,
    textAlign: 'center',
  },

  numero: {
    fontSize: 80,
    color: '#fff',
  },

  boxBotao: {
    width: 200,
  },
});

const Titulo = () => {
  return (
    <View style={estilo.boxTitulo}>
      <Text style={estilo.tituloCabecalho}>
        Sorteio DevMedia
      </Text>

      <Text style={estilo.subtitulo}>
        Hora de ver quem é o vencedor
      </Text>
    </View>
  );
};

const TelaInicial = () => {
  const [numeroSorteado, setNumeroSorteado] = useState(0);

  const gerarNumero = () => {
    const novoNumero = Math.floor(Math.random() * 100 + 1);

    setNumeroSorteado(novoNumero);
  };

  return (
    <View style={estilo.tela}>

      <Text style={estilo.tituloTexto}>
        Toque no botão e veja quem é o vencedor de 1 à 100
      </Text>

      <View style={estilo.boxNumero}>
        <Text style={estilo.numero}>
          {numeroSorteado}
        </Text>
      </View>

      <View style={estilo.boxBotao}>
        <Button
          title="Sortear"
          onPress={gerarNumero}
          color="#1f4f66"
        />
      </View>

    </View>
  );
};

const App = () => {
  return (
    <View>
      <Titulo />
      <TelaInicial />
    </View>
  );
};

export default App;
```

---

# 25. Por que o número muda na tela?

Esta é uma das perguntas mais importantes para compreender o projeto.

Observe:

```javascript
const [numeroSorteado, setNumeroSorteado] = useState(0);
```

O valor é exibido aqui:

```javascript
<Text>
  {numeroSorteado}
</Text>
```

Quando o botão é pressionado:

```javascript
onPress={gerarNumero}
```

a função é executada:

```javascript
const gerarNumero = () => {
  const novoNumero = Math.floor(Math.random() * 100 + 1);

  setNumeroSorteado(novoNumero);
};
```

A função:

```javascript
setNumeroSorteado()
```

altera o estado.

O React identifica essa alteração e renderiza novamente o componente.

Na nova renderização:

```javascript
{numeroSorteado}
```

possui o novo valor.

Por isso o número apresentado na tela muda.

---

# 26. O ciclo completo

Podemos resumir o funcionamento da aplicação em quatro etapas:

### 1. Estado

```javascript
const [numeroSorteado, setNumeroSorteado] = useState(0);
```

Existe um estado com valor inicial `0`.

### 2. Interface

```javascript
<Text>
  {numeroSorteado}
</Text>
```

A interface apresenta o estado.

### 3. Evento

```javascript
onPress={gerarNumero}
```

O botão reage ao toque do usuário.

### 4. Atualização

```javascript
setNumeroSorteado(novoNumero);
```

O estado é alterado e a interface é atualizada.

Podemos visualizar:

```text
             ┌───────────────┐
             │    ESTADO     │
             │ numeroSorteado│
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │   INTERFACE   │
             │  mostra valor │
             └───────┬───────┘
                     │
                     │ usuário interage
                     ▼
             ┌───────────────┐
             │    EVENTO     │
             │    onPress    │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │    FUNÇÃO     │
             │ gerarNumero() │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ setNumero...  │
             └───────┬───────┘
                     │
                     ▼
               ESTADO MUDA
                     │
                     └───────────────→ nova renderização
```

---

# 27. `Button` e estilização

O React Native possui componentes nativos, como:

```javascript
<Button />
```

O `Button` possui comportamento e aparência que podem variar de acordo com a plataforma.

Por exemplo, a aparência pode ser diferente entre Android e iOS.

Por isso, diferentemente de componentes como `View` e `Text`, a propriedade `style` não é utilizada da mesma maneira para personalizar completamente o `Button`.

Podemos, por exemplo, alterar sua cor:

```javascript
<Button
  title="Sortear"
  color="#1f4f66"
/>
```

Quando precisamos de maior controle visual sobre um botão, podemos utilizar componentes como `Pressable` e criar nossa própria aparência.

---

# 28. Estado x variável comum

É importante não confundir os dois conceitos.

### Variável comum

```javascript
let contador = 0;
```

É uma variável JavaScript comum.

### Estado

```javascript
const [contador, setContador] = useState(0);
```

É um estado controlado pelo React.

A principal diferença é que o estado está integrado ao mecanismo de renderização do React.

Quando fazemos:

```javascript
setContador(10);
```

estamos informando ao React que o estado deve ser atualizado.

---

# 29. Erros comuns

## Erro 1 — Alterar o estado diretamente

Evite:

```javascript
numeroSorteado = 50;
```

Utilize:

```javascript
setNumeroSorteado(50);
```

---

## Erro 2 — Executar a função imediatamente no `onPress`

Evite:

```javascript
onPress={gerarNumero()}
```

Prefira:

```javascript
onPress={gerarNumero}
```

---

## Erro 3 — Esquecer de importar `useState`

Se utilizarmos:

```javascript
useState(0)
```

precisamos importar o Hook:

```javascript
import React, { useState } from 'react';
```

---

## Erro 4 — Tentar utilizar `onPress` em qualquer componente

Nem todos os componentes possuem comportamento de toque.

Utilize componentes que suportem interação, como:

```text
Button
Pressable
TouchableOpacity
TouchableHighlight
```

---

# 30. Conceitos fundamentais para memorizar

### `useState`

Cria um estado no componente.

```javascript
const [valor, setValor] = useState(valorInicial);
```

---

### Estado

Representa uma informação que pode mudar durante a execução da aplicação e cuja alteração deve ser refletida na interface.

---

### Função de atualização

É utilizada para alterar o estado:

```javascript
setValor(novoValor);
```

---

### `onPress`

Define o que deve acontecer quando um componente interativo for pressionado:

```javascript
<Button
  title="Sortear"
  onPress={gerarNumero}
/>
```

---

### Renderização

Quando o estado utilizado pelo componente é atualizado, o React pode renderizar o componente novamente para refletir o novo estado na interface.

---

# 31. Resumo da aula

Nesta aula aprendemos que:

* Componentes podem possuir **estado**;
* O Hook `useState` permite criar e controlar esse estado;
* `useState` fornece o valor atual e uma função para atualizá-lo;
* O estado deve ser atualizado utilizando sua função de atualização;
* `onPress` permite responder a ações de toque;
* Podemos associar uma função ao `onPress`;
* A função executada pelo evento pode alterar o estado;
* Quando o estado muda, o React atualiza a interface conforme necessário;
* `Math.random()` pode ser utilizado para gerar valores aleatórios;
* `Math.floor()` pode transformar valores decimais em números inteiros;
* Estado e eventos são fundamentais para criar interfaces interativas.

---

# 32. O conceito mais importante

Mais importante do que decorar:

```javascript
useState
```

ou:

```javascript
onPress
```

é compreender a relação entre eles.

Uma aplicação interativa normalmente segue uma lógica semelhante a:

```text
AÇÃO DO USUÁRIO
       ↓
     EVENTO
       ↓
     FUNÇÃO
       ↓
 ALTERAÇÃO DO ESTADO
       ↓
 NOVA RENDERIZAÇÃO
       ↓
INTERFACE ATUALIZADA
```

No nosso aplicativo:

```text
Toque em "Sortear"
       ↓
     onPress
       ↓
  gerarNumero()
       ↓
setNumeroSorteado()
       ↓
estado atualizado
       ↓
React renderiza novamente
       ↓
novo número aparece
```

**Esse fluxo será utilizado repetidamente em aplicações React Native.**
# React Native — Estado e Eventos de Toque

## 1. Introdução

Até aqui, aprendemos a criar componentes React Native e utilizar `props` para passar informações entre eles.

Nesta etapa, vamos aprender dois conceitos fundamentais para criar aplicativos **interativos**:

* **Estado (`state`)**
* **Eventos de toque (`onPress`)**

Esses dois conceitos trabalham juntos para permitir que o aplicativo **reaja às ações do usuário**.

Como exemplo, vamos criar um aplicativo que sorteia um número entre **1 e 100** sempre que o usuário tocar em um botão.

---

## 2. O que vamos aprender

Ao final deste conteúdo, você deverá compreender:

* O que é uma variável de estado;
* O que são Hooks;
* Como utilizar o Hook `useState`;
* Como alterar o estado de um componente;
* O que é o evento `onPress`;
* Como executar uma função quando um botão é pressionado;
* Como uma alteração de estado provoca uma nova renderização da interface;
* Como gerar números aleatórios em JavaScript;
* Como combinar estado e eventos para criar uma interface interativa.

---

# 3. O que é estado?

Em uma aplicação, existem informações que podem mudar durante sua execução.

Por exemplo:

* nome de um usuário;
* quantidade de produtos em um carrinho;
* situação de um botão;
* texto digitado em um campo;
* número sorteado em um jogo;
* contador de pontos.

Essas informações podem ser chamadas de **estado** da aplicação ou de um componente.

No React Native, utilizamos o **State** para armazenar informações que podem mudar e que precisam ser refletidas na interface.

### Exemplo

Imagine que temos inicialmente:

```text
Número: 0
```

O usuário toca no botão:

```text
Sortear
```

O aplicativo gera:

```text
Número: 73
```

O valor mudou.

Precisamos então de uma forma de informar ao React Native:

> "O valor mudou. Atualize a interface."

É exatamente nesse cenário que utilizamos o `useState`.

---

# 4. O Hook `useState`

O React fornece recursos chamados **Hooks**.

Hooks são funções especiais que permitem utilizar determinados recursos do React dentro de componentes funcionais.

Um dos Hooks mais utilizados é:

```javascript
useState
```

Ele permite criar e controlar uma variável de estado.

Para utilizá-lo, fazemos a importação:

```javascript
import React, { useState } from 'react';
```

Depois podemos criar um estado:

```javascript
const [numero, setNumero] = useState(0);
```

Nesse exemplo temos:

```text
numero
   ↓
valor atual do estado

setNumero
   ↓
função utilizada para alterar o estado

useState(0)
   ↓
valor inicial do estado
```

---

# 5. Entendendo o `useState`

Observe:

```javascript
const [numero, setNumero] = useState(0);
```

Podemos interpretar essa instrução da seguinte maneira:

```text
┌─────────────────────────────────────┐
│             useState(0)             │
│                                     │
│        Estado inicial = 0           │
└──────────────────┬──────────────────┘
                   │
                   ▼
          ┌─────────────────┐
          │      numero     │
          │   valor atual   │
          └─────────────────┘
                   │
                   │ alteração
                   ▼
          ┌─────────────────┐
          │    setNumero    │
          │ função que muda │
          │     o estado    │
          └─────────────────┘
```

O primeiro elemento representa o **valor atual**.

O segundo representa a **função utilizada para atualizar esse valor**.

Por convenção, usamos nomes como:

```javascript
const [nome, setNome] = useState('');
const [idade, setIdade] = useState(0);
const [contador, setContador] = useState(0);
```

O padrão normalmente é:

```text
[valor, setValor]
```

---

# 6. Por que não utilizar uma variável comum?

Poderíamos pensar em fazer:

```javascript
let numero = 0;
```

E depois:

```javascript
numero = 50;
```

Mas isso não é suficiente para controlar uma informação que precisa ser exibida na interface.

Quando o valor utilizado pela interface muda, precisamos que o React saiba que deve **renderizar novamente o componente**.

Por isso utilizamos:

```javascript
const [numero, setNumero] = useState(0);
```

Quando fazemos:

```javascript
setNumero(50);
```

o React é informado de que o estado mudou.

Como consequência, o componente é renderizado novamente utilizando o novo valor.

---

# 7. Estado e renderização

Considere o seguinte componente:

```javascript
const Tela = () => {
  const [numero, setNumero] = useState(0);

  return (
    <Text>{numero}</Text>
  );
};
```

Inicialmente:

```text
numero = 0
```

A tela apresenta:

```text
0
```

Quando executamos:

```javascript
setNumero(50);
```

o estado passa a ser:

```text
numero = 50
```

O React renderiza o componente novamente.

A tela passa a apresentar:

```text
50
```

Podemos representar o processo assim:

```text
setNumero(50)
      ↓
estado é atualizado
      ↓
React identifica a alteração
      ↓
componente é renderizado novamente
      ↓
novo valor aparece na interface
```

Esse é um dos conceitos mais importantes desta aula.

---

# 8. Desestruturação de arrays

A criação do estado utiliza um recurso da linguagem JavaScript chamado **desestruturação**.

Por exemplo:

```javascript
const tecnologias = ['JavaScript', 'React'];

const [linguagem, frontend] = tecnologias;
```

Agora:

```javascript
linguagem
```

contém:

```text
JavaScript
```

E:

```javascript
frontend
```

contém:

```text
React
```

Isso acontece porque os valores do array são atribuídos às variáveis de acordo com sua posição.

```text
tecnologias
     │
     ├── posição 0 → JavaScript
     │
     └── posição 1 → React

        ↓ desestruturação

linguagem = JavaScript
frontend  = React
```

O `useState` utiliza esse mesmo conceito:

```javascript
const [numero, setNumero] = useState(0);
```

O `useState` retorna dois valores:

```text
valor atual
função de atualização
```

A desestruturação permite atribuir esses dois valores às variáveis:

```text
numero
setNumero
```

---

# 9. O que são Hooks?

Hooks são funções especiais disponibilizadas pelo React para permitir que componentes funcionais utilizem recursos do React.

Alguns exemplos conhecidos são:

```javascript
useState
useEffect
useContext
```

Nesta aula vamos trabalhar especificamente com:

```javascript
useState
```

Uma característica importante dos Hooks é que eles devem ser utilizados seguindo as regras definidas pelo React.

Por exemplo, o `useState` normalmente é declarado diretamente dentro do componente:

```javascript
const TelaInicial = () => {
  const [numero, setNumero] = useState(0);

  // ...
};
```

Não devemos criar o estado dentro de estruturas condicionais ou loops:

```javascript
// Evite fazer isso
if (condicao) {
  const [numero, setNumero] = useState(0);
}
```

Para esta etapa, o mais importante é compreender:

> `useState` permite que o componente mantenha um valor entre suas renderizações e seja atualizado quando esse valor mudar.

---

# 10. O que é um evento?

Um evento representa uma ação que acontece durante a utilização da aplicação.

Exemplos:

* tocar em um botão;
* pressionar uma área da tela;
* digitar em um campo;
* alterar um campo;
* selecionar uma opção.

Em uma aplicação mobile, uma das ações mais comuns é o **toque**.

No React Native, vários componentes oferecem propriedades para responder a interações do usuário.

Uma delas é:

```javascript
onPress
```

---

# 11. O evento `onPress`

O `onPress` permite definir uma função que será executada quando o usuário tocar em determinado componente que suporta esse evento.

Exemplo:

```javascript
<Button
  title="Clique aqui"
  onPress={minhaFuncao}
/>
```

Nesse caso, quando o usuário tocar no botão, a função:

```javascript
minhaFuncao
```

será executada.

Podemos representar:

```text
Usuário toca no botão
          ↓
       onPress
          ↓
   minhaFuncao()
          ↓
      ação executada
```

---

# 12. `onPress` e funções

Podemos criar uma função para executar uma determinada ação:

```javascript
const mostrarMensagem = () => {
  console.log('Botão pressionado');
};
```

Depois associamos essa função ao botão:

```javascript
<Button
  title="Clique aqui"
  onPress={mostrarMensagem}
/>
```

Quando o botão for pressionado:

```text
Usuário
   ↓
toca no botão
   ↓
onPress
   ↓
mostrarMensagem()
   ↓
"Botão pressionado"
```

---

# 13. Uma atenção importante com `onPress`

Observe:

```javascript
onPress={mostrarMensagem}
```

Estamos passando a **função**.

Não devemos, nesse caso, fazer:

```javascript
onPress={mostrarMensagem()}
```

A diferença é importante.

### Passando a função

```javascript
onPress={mostrarMensagem}
```

Significa:

> "Quando acontecer o evento, execute essa função."

### Executando imediatamente

```javascript
onPress={mostrarMensagem()}
```

Significa:

> "Execute essa função agora e utilize o resultado dela."

Portanto, quando queremos associar uma função diretamente ao `onPress`, utilizamos:

```javascript
onPress={mostrarMensagem}
```

---

# 14. Quais componentes possuem `onPress`?

Não podemos assumir que qualquer componente possui a propriedade `onPress`.

Alguns componentes que permitem interação por toque incluem:

* `Button`
* `Pressable`
* `TouchableOpacity`
* `TouchableHighlight`

Por exemplo:

```javascript
<Button
  title="Sortear"
  onPress={gerarNumero}
/>
```

O componente `Button` possui suporte ao `onPress`.

---

# 15. Criando o aplicativo de sorteio

Agora vamos juntar os dois conceitos principais:

```text
useState
+
onPress
```

Nosso objetivo será criar:

```text
┌─────────────────────────────┐
│       Sorteio DevMedia      │
│ Hora de ver quem é vencedor │
├─────────────────────────────┤
│                             │
│  Toque no botão e veja quem │
│  é o vencedor de 1 à 100    │
│                             │
│           ┌─────┐           │
│           │  73 │           │
│           └─────┘           │
│                             │
│         [ Sortear ]         │
│                             │
└─────────────────────────────┘
```

Quando o usuário tocar em **Sortear**, um novo número deverá aparecer.

---

# 16. Criando o estado `numeroSorteado`

Primeiro importamos o `useState`:

```javascript
import React, { useState } from 'react';
```

Depois criamos o estado:

```javascript
const [numeroSorteado, setNumeroSorteado] = useState(0);
```

Temos:

| Elemento            | Função                     |
| ------------------- | -------------------------- |
| `numeroSorteado`    | valor atual do número      |
| `setNumeroSorteado` | função que altera o estado |
| `0`                 | valor inicial              |

Podemos exibir o estado na tela:

```javascript
<Text>
  {numeroSorteado}
</Text>
```

Inicialmente teremos:

```text
0
```

---

# 17. Criando a função `gerarNumero`

Agora precisamos criar uma função que gere um número aleatório.

```javascript
const gerarNumero = () => {
  const novoNumero = Math.floor(Math.random() * (101 - 1) + 1);

  setNumeroSorteado(novoNumero);
};
```

Vamos analisar cada parte.

---

# 18. `Math.random()`

A função:

```javascript
Math.random()
```

gera um número aleatório maior ou igual a `0` e menor que `1`.

Exemplos possíveis:

```text
0.13
0.58
0.91
0.42
```

Ela nunca retorna exatamente `1`.

---

# 19. `Math.floor()`

A função:

```javascript
Math.floor()
```

arredonda um número para baixo, retornando o maior número inteiro menor ou igual ao valor informado.

Exemplo:

```javascript
Math.floor(4.8);
```

Resultado:

```text
4
```

Outro exemplo:

```javascript
Math.floor(9.99);
```

Resultado:

```text
9
```

---

# 20. Gerando um número entre 1 e 100

Utilizamos:

```javascript
Math.floor(Math.random() * (101 - 1) + 1);
```

Podemos simplificar matematicamente:

```javascript
Math.floor(Math.random() * 100 + 1);
```

O resultado será um número inteiro entre:

```text
1
```

e:

```text
100
```

inclusive.

A lógica é:

```text
Math.random()
      ↓
número entre 0 e menor que 1
      ↓
× 100
      ↓
número entre 0 e menor que 100
      ↓
+ 1
      ↓
número entre 1 e menor que 101
      ↓
Math.floor()
      ↓
inteiro entre 1 e 100
```

---

# 21. Atualizando o estado

Depois de gerar o número, precisamos atualizar o estado:

```javascript
setNumeroSorteado(novoNumero);
```

Por exemplo, se:

```javascript
novoNumero = 73;
```

teremos:

```javascript
setNumeroSorteado(73);
```

O estado será atualizado:

```text
numeroSorteado = 73
```

E o React Native poderá atualizar a interface.

---

# 22. Associando a função ao botão

Agora basta associar a função ao `onPress`:

```javascript
<Button
  title="Sortear"
  onPress={gerarNumero}
/>
```

O fluxo completo passa a ser:

```text
Usuário toca em "Sortear"
             ↓
          onPress
             ↓
        gerarNumero()
             ↓
        Math.random()
             ↓
        novoNumero
             ↓
   setNumeroSorteado()
             ↓
       estado alterado
             ↓
   componente renderizado
             ↓
    novo número exibido
```

Esse é o funcionamento central do nosso aplicativo.

---

# 23. Código completo do componente

O componente `TelaInicial` pode ficar assim:

```javascript
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';
import estilo from './estilo';

const TelaInicial = () => {
  const [numeroSorteado, setNumeroSorteado] = useState(0);

  const gerarNumero = () => {
    const novoNumero = Math.floor(Math.random() * 100 + 1);

    setNumeroSorteado(novoNumero);
  };

  return (
    <View style={estilo.tela}>

      <Text style={estilo.tituloTexto}>
        Toque no botão e veja quem é o vencedor de 1 à 100
      </Text>

      <View style={estilo.boxNumero}>
        <Text style={estilo.numero}>
          {numeroSorteado}
        </Text>
      </View>

      <View style={estilo.boxBotao}>
        <Button
          title="Sortear"
          onPress={gerarNumero}
          color="#1f4f66"
        />
      </View>

    </View>
  );
};

export default TelaInicial;
```

---

# 24. O código completo da aplicação

Uma versão simplificada da aplicação pode ser construída assim:

```javascript
import React, { useState } from 'react';
import { View, Text, Button, StyleSheet } from 'react-native';

const estilo = StyleSheet.create({
  boxTitulo: {
    height: 80,
    backgroundColor: '#1f4f66',
    paddingHorizontal: 10,
    paddingTop: 10,
    justifyContent: 'center',
  },

  tituloCabecalho: {
    color: '#0fc3d4',
    fontWeight: '700',
    fontSize: 20,
  },

  subtitulo: {
    color: '#fff',
  },

  tela: {
    width: '100%',
    justifyContent: 'center',
    alignItems: 'center',
  },

  boxNumero: {
    borderColor: '#13b0c5',
    backgroundColor: '#13b0c5',
    borderWidth: 5,
    height: 150,
    width: 150,
    borderRadius: 75,
    justifyContent: 'center',
    alignItems: 'center',
    marginBottom: 50,
  },

  tituloTexto: {
    fontSize: 14,
    marginVertical: 30,
    paddingHorizontal: 20,
    textAlign: 'center',
  },

  numero: {
    fontSize: 80,
    color: '#fff',
  },

  boxBotao: {
    width: 200,
  },
});

const Titulo = () => {
  return (
    <View style={estilo.boxTitulo}>
      <Text style={estilo.tituloCabecalho}>
        Sorteio DevMedia
      </Text>

      <Text style={estilo.subtitulo}>
        Hora de ver quem é o vencedor
      </Text>
    </View>
  );
};

const TelaInicial = () => {
  const [numeroSorteado, setNumeroSorteado] = useState(0);

  const gerarNumero = () => {
    const novoNumero = Math.floor(Math.random() * 100 + 1);

    setNumeroSorteado(novoNumero);
  };

  return (
    <View style={estilo.tela}>

      <Text style={estilo.tituloTexto}>
        Toque no botão e veja quem é o vencedor de 1 à 100
      </Text>

      <View style={estilo.boxNumero}>
        <Text style={estilo.numero}>
          {numeroSorteado}
        </Text>
      </View>

      <View style={estilo.boxBotao}>
        <Button
          title="Sortear"
          onPress={gerarNumero}
          color="#1f4f66"
        />
      </View>

    </View>
  );
};

const App = () => {
  return (
    <View>
      <Titulo />
      <TelaInicial />
    </View>
  );
};

export default App;
```

---

# 25. Por que o número muda na tela?

Esta é uma das perguntas mais importantes para compreender o projeto.

Observe:

```javascript
const [numeroSorteado, setNumeroSorteado] = useState(0);
```

O valor é exibido aqui:

```javascript
<Text>
  {numeroSorteado}
</Text>
```

Quando o botão é pressionado:

```javascript
onPress={gerarNumero}
```

a função é executada:

```javascript
const gerarNumero = () => {
  const novoNumero = Math.floor(Math.random() * 100 + 1);

  setNumeroSorteado(novoNumero);
};
```

A função:

```javascript
setNumeroSorteado()
```

altera o estado.

O React identifica essa alteração e renderiza novamente o componente.

Na nova renderização:

```javascript
{numeroSorteado}
```

possui o novo valor.

Por isso o número apresentado na tela muda.

---

# 26. O ciclo completo

Podemos resumir o funcionamento da aplicação em quatro etapas:

### 1. Estado

```javascript
const [numeroSorteado, setNumeroSorteado] = useState(0);
```

Existe um estado com valor inicial `0`.

### 2. Interface

```javascript
<Text>
  {numeroSorteado}
</Text>
```

A interface apresenta o estado.

### 3. Evento

```javascript
onPress={gerarNumero}
```

O botão reage ao toque do usuário.

### 4. Atualização

```javascript
setNumeroSorteado(novoNumero);
```

O estado é alterado e a interface é atualizada.

Podemos visualizar:

```text
             ┌───────────────┐
             │    ESTADO     │
             │ numeroSorteado│
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │   INTERFACE   │
             │  mostra valor │
             └───────┬───────┘
                     │
                     │ usuário interage
                     ▼
             ┌───────────────┐
             │    EVENTO     │
             │    onPress    │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │    FUNÇÃO     │
             │ gerarNumero() │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ setNumero...  │
             └───────┬───────┘
                     │
                     ▼
               ESTADO MUDA
                     │
                     └───────────────→ nova renderização
```

---

# 27. `Button` e estilização

O React Native possui componentes nativos, como:

```javascript
<Button />
```

O `Button` possui comportamento e aparência que podem variar de acordo com a plataforma.

Por exemplo, a aparência pode ser diferente entre Android e iOS.

Por isso, diferentemente de componentes como `View` e `Text`, a propriedade `style` não é utilizada da mesma maneira para personalizar completamente o `Button`.

Podemos, por exemplo, alterar sua cor:

```javascript
<Button
  title="Sortear"
  color="#1f4f66"
/>
```

Quando precisamos de maior controle visual sobre um botão, podemos utilizar componentes como `Pressable` e criar nossa própria aparência.

---

# 28. Estado x variável comum

É importante não confundir os dois conceitos.

### Variável comum

```javascript
let contador = 0;
```

É uma variável JavaScript comum.

### Estado

```javascript
const [contador, setContador] = useState(0);
```

É um estado controlado pelo React.

A principal diferença é que o estado está integrado ao mecanismo de renderização do React.

Quando fazemos:

```javascript
setContador(10);
```

estamos informando ao React que o estado deve ser atualizado.

---

# 29. Erros comuns

## Erro 1 — Alterar o estado diretamente

Evite:

```javascript
numeroSorteado = 50;
```

Utilize:

```javascript
setNumeroSorteado(50);
```

---

## Erro 2 — Executar a função imediatamente no `onPress`

Evite:

```javascript
onPress={gerarNumero()}
```

Prefira:

```javascript
onPress={gerarNumero}
```

---

## Erro 3 — Esquecer de importar `useState`

Se utilizarmos:

```javascript
useState(0)
```

precisamos importar o Hook:

```javascript
import React, { useState } from 'react';
```

---

## Erro 4 — Tentar utilizar `onPress` em qualquer componente

Nem todos os componentes possuem comportamento de toque.

Utilize componentes que suportem interação, como:

```text
Button
Pressable
TouchableOpacity
TouchableHighlight
```

---

# 30. Conceitos fundamentais para memorizar

### `useState`

Cria um estado no componente.

```javascript
const [valor, setValor] = useState(valorInicial);
```

---

### Estado

Representa uma informação que pode mudar durante a execução da aplicação e cuja alteração deve ser refletida na interface.

---

### Função de atualização

É utilizada para alterar o estado:

```javascript
setValor(novoValor);
```

---

### `onPress`

Define o que deve acontecer quando um componente interativo for pressionado:

```javascript
<Button
  title="Sortear"
  onPress={gerarNumero}
/>
```

---

### Renderização

Quando o estado utilizado pelo componente é atualizado, o React pode renderizar o componente novamente para refletir o novo estado na interface.

---

# 31. Resumo da aula

Nesta aula aprendemos que:

* Componentes podem possuir **estado**;
* O Hook `useState` permite criar e controlar esse estado;
* `useState` fornece o valor atual e uma função para atualizá-lo;
* O estado deve ser atualizado utilizando sua função de atualização;
* `onPress` permite responder a ações de toque;
* Podemos associar uma função ao `onPress`;
* A função executada pelo evento pode alterar o estado;
* Quando o estado muda, o React atualiza a interface conforme necessário;
* `Math.random()` pode ser utilizado para gerar valores aleatórios;
* `Math.floor()` pode transformar valores decimais em números inteiros;
* Estado e eventos são fundamentais para criar interfaces interativas.

---

# 32. O conceito mais importante

Mais importante do que decorar:

```javascript
useState
```

ou:

```javascript
onPress
```

é compreender a relação entre eles.

Uma aplicação interativa normalmente segue uma lógica semelhante a:

```text
AÇÃO DO USUÁRIO
       ↓
     EVENTO
       ↓
     FUNÇÃO
       ↓
 ALTERAÇÃO DO ESTADO
       ↓
 NOVA RENDERIZAÇÃO
       ↓
INTERFACE ATUALIZADA
```

No nosso aplicativo:

```text
Toque em "Sortear"
       ↓
     onPress
       ↓
  gerarNumero()
       ↓
setNumeroSorteado()
       ↓
estado atualizado
       ↓
React renderiza novamente
       ↓
novo número aparece
```

**Esse fluxo será utilizado repetidamente em aplicações React Native.**