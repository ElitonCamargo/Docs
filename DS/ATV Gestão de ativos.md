# Atividade Avaliativa — Arquitetura de Software, POO e Acesso a Banco de Dados com C#

**Disciplina:** Desenvolvimento de Sistemas  
**Conteúdo:** Programação Orientada a Objetos, arquitetura de software e acesso ao MySQL com C#  
**Quantidade de questões:** 10  
**Valor sugerido:** 10 pontos

---

## Identificação do aluno

- **Nome:** ______________________________________________
- **Turma:** __________________
- **Data:** ____/____/________

## Orientações

Leia atentamente cada questão e responda utilizando suas próprias palavras.

As respostas devem demonstrar compreensão dos conceitos estudados durante as aulas. Sempre que possível, utilize exemplos do projeto de gestão de ativos para justificar suas respostas.

Não serão consideradas respostas que apenas reproduzam definições sem demonstrar compreensão.

---

## Questões

### 1. Programação Orientada a Objetos (POO)

Durante a implementação do projeto, criamos diferentes classes, como `Ativo`, `Crud` e `AtivoRepository`.

Explique o que é uma classe na Programação Orientada a Objetos e qual é a diferença entre uma classe e um objeto. Utilize a classe `Ativo` para exemplificar sua resposta.

### 2. Encapsulamento e responsabilidade das classes

Na primeira versão do projeto, a classe `Ativos` possuía tanto os atributos que representavam um ativo quanto o método responsável por cadastrá-lo no banco de dados.

Posteriormente, separamos essas responsabilidades entre as classes `Ativo` e `AtivoRepository`.

Explique por que essa separação é importante e quais vantagens ela proporciona para a organização e manutenção do código.

### 3. Herança

No projeto, criamos uma classe chamada `Crud` e utilizamos a herança para permitir que `AtivoRepository` aproveitasse seus métodos.

Observe o exemplo:

```csharp
class AtivoRepository : Crud
{
    // Implementação do repositório
}
```

Explique o conceito de herança em C# e por que utilizamos esse recurso nesse exemplo.

Qual é a vantagem de permitir que diferentes repositórios herdem da mesma classe-base?

### 4. Modificadores de acesso

Na classe `Crud`, utilizamos o modificador de acesso `protected` em alguns métodos.

Explique a diferença entre os modificadores `private`, `public` e `protected`.

Por que o modificador `protected` é adequado para métodos que devem ser utilizados pelas classes que herdam de `Crud`, mas não precisam ser acessados diretamente pelos formulários da aplicação?

### 5. Bibliotecas e namespaces em C#

Durante a implementação, utilizamos:

```csharp
using MySql.Data.MySqlClient;
```

Explique o que é uma biblioteca de software e qual é a finalidade dessa instrução no código C#.

Cite pelo menos duas classes disponibilizadas por essa biblioteca que utilizamos no projeto e explique a finalidade de cada uma delas.

### 6. Conexão com o banco de dados

Para executar operações no MySQL, utilizamos a classe `MySqlConnection`.

Explique qual é a responsabilidade dessa classe e por que precisamos estabelecer uma conexão com o banco de dados antes de executar comandos SQL.

O que poderia acontecer se uma aplicação tentasse executar uma consulta sem estabelecer uma conexão válida?

### 7. Execução de comandos SQL

Em nosso projeto, utilizamos a classe `MySqlCommand` para executar instruções SQL.

Explique qual é a finalidade dessa classe e qual é a diferença entre os métodos `ExecuteNonQuery()` e `ExecuteReader()`.

Em quais situações cada um deles pode ser utilizado?

### 8. Parâmetros SQL e segurança

Na primeira implementação do cadastro de ativos, os valores eram inseridos diretamente na instrução SQL por meio de concatenação de strings.

Posteriormente, passamos a utilizar parâmetros, como:

```csharp
cmd.Parameters.AddWithValue("@nome", ativo.Nome);
```

Explique por que a utilização de parâmetros SQL é mais segura do que concatenar diretamente os valores recebidos do usuário.

O que é uma injeção de SQL (*SQL Injection*) e como a utilização de parâmetros ajuda a prevenir esse tipo de vulnerabilidade?

### 9. Reutilização de código e classe-base `Crud`

Imagine que precisamos desenvolver os repositórios `FuncionarioRepository`, `UsuarioRepository` e `EmprestimoRepository`.

Todos eles precisam executar operações no banco de dados, como inserir, consultar, atualizar e excluir registros.

Explique como a herança da classe `Crud` pode ajudar na implementação desses repositórios.

Por que não seria interessante implementar novamente toda a lógica de conexão e execução de comandos SQL em cada um deles?

### 10. Arquitetura e organização do software

Considere a seguinte situação:

Um programador decide colocar todo o código do sistema dentro de uma única classe, incluindo os atributos dos ativos, comandos SQL, conexão com o banco de dados e código responsável pela interface gráfica.

Explique quais problemas essa decisão pode causar no desenvolvimento e na manutenção do sistema.

Com base no que estudamos, explique como a separação entre `Models`, `Repository` e `Database` contribui para uma aplicação mais organizada e fácil de manter.

---

## Critérios de avaliação

| Critério | Pontuação |
|---|---:|
| Compreensão dos conceitos de POO | 2,0 |
| Compreensão da biblioteca MySql.Data | 2,0 |
| Compreensão do acesso e execução de SQL | 2,0 |
| Segurança e boas práticas | 2,0 |
| Arquitetura e organização do software | 2,0 |
| **Total** | **10,0** |

## Considerações finais

O objetivo desta atividade é verificar se você compreendeu os conceitos utilizados na construção do projeto de gestão de ativos.

Mais importante do que memorizar comandos ou definições é compreender:

- Por que utilizamos classes e objetos.
- Como a herança permite reutilizar código.
- Como organizamos as responsabilidades de uma aplicação.
- Como C# realiza a comunicação com um banco de dados MySQL.
- Por que devemos utilizar boas práticas de segurança e organização de código.

**Responda com suas próprias palavras e demonstre que você compreendeu os conceitos estudados.**
