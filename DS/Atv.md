## Prova de POO

A seguir estão 30 questões de múltipla escolha com 4 alternativas cada, baseadas nos conceitos de programação orientada a objetos trabalhados nos exemplos de classes, herança, encapsulamento, polimorfismo, interfaces e validações.

### 1) Em POO, o principal objetivo do encapsulamento é:
A) Permitir que qualquer classe altere diretamente os atributos de outra.
B) Controlar o acesso e a validação dos dados internos da classe.
C) Substituir totalmente o uso de métodos.
D) Tornar todas as propriedades públicas por padrão.

### 2) Considere uma classe base com um método virtual e uma classe derivada que o sobrescreve. O que acontece quando um objeto da classe derivada é referenciado por uma variável do tipo base?
A) O método da base sempre executa.
B) O método sobrescrito da derivada executa por polimorfismo.
C) O compilador rejeita a atribuição.
D) O método é ignorado e a classe deixa de funcionar.

### 3) Qual é a diferença principal entre uma interface e uma classe abstrata?
A) Interface pode ter atributos concretos; classe abstrata não.
B) Classe abstrata nunca pode ter métodos abstratos; interface sempre tem implementações.
C) Interface define contrato; classe abstrata pode conter implementação parcial e estados.
D) Não existe diferença prática entre elas em C#.

### 4) Em C#, um construtor de uma classe derivada normalmente usa:
A) `base` para chamar o construtor da classe base.
B) `this` para acessar o objeto pai.
C) `new` para instanciar a classe base.
D) `override` para chamar o construtor base.

### 5) Se uma propriedade inclui validação no setter, isso é um exemplo de:
A) Herança múltipla.
B) Encapsulamento com regra de negócio.
C) Delegação de método.
D) Polimorfismo por sobrecarga.

### 6) Qual das alternativas melhor representa o uso correto de `this`?
A) `this = valor;`
B) `this.Nome = nome;`
C) `this.void Metodo();`
D) `this() = construtor;`

### 7) Quando uma classe define vários métodos com o mesmo nome, mas com parâmetros diferentes, isso é chamado de:
A) Sobrescrita.
B) Delegação.
C) Sobrecarga.
D) Herança.

### 8) Em um método `Transferir`, se a conta de destino for `null`, o código correto é:
A) Ignorar a operação e continuar.
B) Lançar uma exceção como `ArgumentNullException`.
C) Criar uma nova conta automaticamente.
D) Cancelar o saldo da conta origem.

### 9) Qual é a principal vantagem de usar `decimal` para valores monetários em vez de `double`?
A) `decimal` é mais rápido em operações financeiras.
B) `decimal` reduz a precisão em cálculos de moeda.
C) `decimal` evita problemas de arredondamento em dinheiro.
D) `double` é obrigatório para valores monetários.

### 10) Em uma conta bancária, se o saldo for insuficiente para saque, o correto é:
A) Permitir o saque e assumir saldo negativo.
B) Lançar exceção para impedir operação inválida.
C) Ignorar a validação.
D) Depositar automaticamente o valor solicitado.

### 11) Em um modelo com `Pessoa` abstrata e `PessoaFisica`, `PessoaJuridica` herdando dela, a classe `Pessoa` provavelmente serve para:
A) Representar apenas um objeto concreto.
B) Definir atributos e regras comuns para todos os tipos de pessoa.
C) Eliminar a necessidade de atributos em subclasses.
D) Permitir instância direta sem construtor.

### 12) Qual das afirmações sobre `abstract class` está correta?
A) Não pode ter métodos.
B) Não pode ser herdada.
C) Não pode ser instanciada diretamente.
D) Só pode ter campos estáticos.

### 13) Em um setter de `Titular`, se o nome contém números, o ideal é:
A) Ignorar o caractere.
B) Validar e lançar exceção.
C) Converter os números para letras.
D) Permitir sem validação.

### 14) Considere esta lógica:
- `this.saldo -= valor;`
- antes da operação, `valor > saldo`.

O que é mais adequado fazer?
A) Executar a subtração sem validação.
B) Validar antes e impedir operação inválida.
C) Trocar o valor por `0`.
D) Reduzir o `saldo` para metade.

### 15) O uso de `Regex` em validações de CPF, CNPJ ou nome é útil porque:
A) Substitui totalmente a necessidade de regras de negócio.
B) Permite validar padrões esperados de entrada.
C) Elimina a necessidade de exceções.
D) Garante que o dado será sempre numérico.

### 16) Em uma lista de contas, se você cria `List<Conta>` e adiciona `ContaCorrente` e `ContaPoupanca`, isso é um exemplo de:
A) Encapsulamento rígido.
B) Polimorfismo por herança.
C) Herança múltipla.
D) Sobrecarga de construtores.

### 17) Qual é a função de `override` em C#?
A) Definir um novo método na própria classe base.
B) Aplicar a implementação específica da subclasse para um método virtual ou abstrato.
C) Impedir que uma classe herde outra.
D) Tornar um método estático.

### 18) O que acontece se um método for declarado `virtual` e a classe derivada não o sobrescrever?
A) O método é removido da classe.
B) A implementação da classe base continua sendo usada.
C) O compilador cria um método abstrato automaticamente.
D) O método vira estático.

### 19) Em um projeto bancário, a validação do número da conta com `if (value.Length < 5)` está relacionado a:
A) Regras de negócio e integridade dos dados.
B) Interface gráfica.
C) Persistência em banco de dados.
D) Organização da UI.

### 20) Qual da alternativa melhor descreve a diferença entre `throw` e `return`?
A) `throw` encerra a execução da rotina e sinaliza erro; `return` encerra a rotina e devolve valor ou nulo.
B) `throw` retorna valor; `return` lança exceção.
C) Ambos são equivalentes em qualquer contexto.
D) `throw` só funciona em métodos estáticos.

### 21) Em que situação o uso de `protected` é mais adequado?
A) Quando o atributo deve ser acessível por qualquer classe do projeto.
B) Quando o atributo deve ser visível apenas dentro da própria classe e subclasses.
C) Quando o atributo deve ser obrigatório para todas as instâncias.
D) Quando o atributo precisa ser dinâmico em tempo de execução.

### 22) Uma classe que implementa uma interface deve:
A) Não declarar membros.
B) Implementar todos os membros exigidos pela interface.
C) Não poder herdar de outra classe.
D) Ser sempre abstrata.

### 23) Qual é o efeito prático de uma classe possuir um construtor com parâmetros e outro sem parâmetros?
A) Isso é impossível em C#.
B) Permite a criação de objetos de maneiras diferentes.
C) Torna a classe automaticamente estática.
D) Exige que os objetos sejam sempre criados em lista.

### 24) Qual é a consequência de um método `sacar(valor)` validar `if (valor <= 0)` antes de verificar saldo?
A) Permite saque de valor zero.
B) Evita operações inconsistentes e inválidas.
C) Cria duplicidade de saldo.
D) Não tem efeito prático.

### 25) Em uma aplicação com múltiplas contas e uma lista de objetos, qual estrutura é mais adequada para armazená-las?
A) `int`
B) `string`
C) `List<Conta>`
D) `char`

### 26) No contexto de herança, um objeto da classe `ContaSalario` pode ser tratado como:
A) `PessoaFisica` apenas.
B) `Conta` e também `Pessoa`.
C) `List<Conta>` apenas.
D) `IContaRendimentos` sempre.

### 27) Considere a operação:
- `contaOrigem.Sacar(valor);`
- `contaDestino.Depositar(valor);`

Qual conceito está sendo demonstrado nesse padrão?
A) Sobrecarga de operador.
B) Encapsulamento e consistência do fluxo financeiro.
C) Herança múltipla.
D) Instanciação direta de objetos.

### 28) Em um sistema com classes `Pessoa`, `PessoaFisica` e `PessoaJuridica`, o uso de `base(nome, endereco, telefone)` no construtor da classe filha representa:
A) Criação de objeto anônimo.
B) Chamada do construtor da classe base.
C) Sobrescrita de um método virtual.
D) Declaração de constante.

### 29) O que torna a sobrecarga de métodos diferente da sobrescrita?
A) Sobrecarrega é redefinir implementação; sobrescrita é criar vários métodos iguais.
B) Sobrecarga altera a assinatura do método; sobrescrita reimplementa um método herdado com mesma assinatura.
C) Sobrecarga exige interface; sobrescrita exige classe abstrata.
D) Não há diferença entre os dois termos.

### 30) A principal razão para usar validação no setter e também no método de operação financeira é:
A) Reduzir a quantidade de atributos da classe.
B) Garantir integridade nos dados e evitar inconsistências de estado.
C) Acelerar a execução da aplicação.
D) Evitar o uso de listas e coleções.

---

## Gabarito

1) B  
2) B  
3) C  
4) A  
5) B  
6) B  
7) C  
8) B  
9) C  
10) B  
11) B  
12) C  
13) B  
14) B  
15) B  
16) B  
17) B  
18) B  
19) A  
20) A  
21) B  
22) B  
23) B  
24) B  
25) C  
26) B  
27) B  
28) B  
29) B  
30) B
