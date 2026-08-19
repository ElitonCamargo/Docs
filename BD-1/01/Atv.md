# Lista de Exercícios — MySQL DDL: Sistema Escolar

## Contexto

Você foi contratado para desenvolver o banco de dados de um sistema escolar.

O sistema deverá controlar:

- **Curso** — representa um curso oferecido pela instituição.
- **Turma** — representa uma turma de um determinado curso.
- **Aluno** — representa os alunos matriculados na instituição.
- **Matrícula** — representa a participação de um aluno em uma turma.

Durante os exercícios, você irá construir e evoluir o banco de dados utilizando comandos **DDL do MySQL**.

> **Comandos trabalhados:** `CREATE DATABASE`, `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`, `DROP DATABASE` e, como complemento, `DELETE`.

---

# Nível 1 — Criando o banco

### Exercício 1 — Criando o banco de dados

Crie um banco de dados chamado:

```text
escola
```

Depois, selecione esse banco para ser utilizado nos próximos exercícios.

**Objetivo:** praticar `CREATE DATABASE` e `USE`.

---

### Exercício 2 — Criando a tabela Curso

Crie uma tabela chamada `curso`.

Ela deverá possuir, inicialmente, os seguintes campos:

| Campo | Tipo |
|---|---|
| id_curso | inteiro |
| nome | texto |
| carga_horaria | inteiro |

Defina `id_curso` como chave primária.

**Objetivo:** praticar `CREATE TABLE`, tipos de dados e `PRIMARY KEY`.

---

### Exercício 3 — Criando a tabela Aluno

Crie a tabela `aluno` com os seguintes campos:

| Campo | Tipo |
|---|---|
| id_aluno | inteiro |
| nome | texto |
| cpf | texto |
| data_nascimento | data |

Defina `id_aluno` como chave primária.

**Desafio:** escolha tamanhos adequados para os campos de texto.

---

### Exercício 4 — Criando a tabela Turma

Crie a tabela `turma`.

Ela deverá possuir:

| Campo | Tipo |
|---|---|
| id_turma | inteiro |
| nome | texto |
| ano | inteiro |
| id_curso | inteiro |

Defina `id_turma` como chave primária.

Por enquanto, não é necessário criar a chave estrangeira.

---

# Nível 2 — Evoluindo as tabelas

Agora imagine que a equipe da escola percebeu que algumas informações estavam faltando.

### Exercício 5 — Adicionando uma coluna

A escola deseja armazenar a **data de início do curso**.

Altere a tabela `curso` adicionando:

```text
data_inicio
```

Utilize um tipo de dado adequado para representar uma data.

**Objetivo:** praticar `ALTER TABLE ... ADD COLUMN`.

---

### Exercício 6 — Modificando uma coluna

Após alguns testes, a equipe percebeu que o nome do curso pode possuir até 150 caracteres.

Altere a coluna `nome` da tabela `curso` para suportar essa quantidade de caracteres.

**Objetivo:** praticar `ALTER TABLE ... MODIFY COLUMN`.

---

### Exercício 7 — Adicionando restrições

A escola determinou novas regras:

- O nome do curso não pode ficar vazio.
- A carga horária deve ser obrigatória.
- O CPF do aluno deve ser obrigatório.
- O nome do aluno deve ser obrigatório.

Altere as tabelas necessárias para implementar essas regras.

**Objetivo:** praticar `NOT NULL`.

---

### Exercício 8 — Criando uma chave estrangeira

Agora é necessário representar uma regra importante:

> Uma turma pertence a um curso.

Altere a tabela `turma` para que `id_curso` seja uma chave estrangeira que referencia `curso(id_curso)`.

**Objetivo:** praticar `FOREIGN KEY`.

**Pergunta para reflexão:**  
Por que é importante impedir que uma turma seja cadastrada para um curso que não existe?

---

# Nível 3 — Criando a matrícula

### Exercício 9 — Criando a tabela de matrícula

Crie uma tabela chamada `matricula`.

Ela deverá possuir:

| Campo | Tipo |
|---|---|
| id_matricula | inteiro |
| id_aluno | inteiro |
| id_turma | inteiro |
| data_matricula | data |

Defina `id_matricula` como chave primária.

---

### Exercício 10 — Relacionando matrícula com aluno e turma

Altere a tabela `matricula` para criar os relacionamentos:

- `id_aluno` referencia `aluno(id_aluno)`
- `id_turma` referencia `turma(id_turma)`

**Objetivo:** praticar mais de uma `FOREIGN KEY`.

Ao terminar, o modelo deverá representar:

```text
CURSO
  │
  └── TURMA
        │
        └── MATRÍCULA
              │
              └── ALUNO
```

---

# Nível 4 — Pensando nas regras do sistema

Agora os exercícios deixam de ser apenas "execute o comando" e passam a exigir que você tome decisões sobre o modelo.

### Exercício 11 — Evitando duplicidade

A escola não deseja permitir dois cursos com exatamente o mesmo nome.

Altere a tabela `curso` para que o campo `nome` seja `UNIQUE`.

Faça o mesmo para o CPF do aluno.

**Objetivo:** praticar `UNIQUE`.

**Pergunta:**  
Qual é a diferença entre `PRIMARY KEY` e `UNIQUE`?

---

### Exercício 12 — Valores padrão

Quando uma matrícula for criada, caso a data da matrícula não seja informada, o banco deverá utilizar automaticamente a data atual.

Altere a tabela `matricula` para implementar esse comportamento.

**Objetivo:** praticar `DEFAULT`.

---

### Exercício 13 — Identificadores automáticos

Atualmente, alguém precisa informar manualmente o `id_curso`, `id_aluno`, `id_turma` e `id_matricula`.

Altere as quatro tabelas para que esses identificadores sejam gerados automaticamente pelo MySQL.

**Objetivo:** praticar `AUTO_INCREMENT`.

---

# Nível 5 — Alterações estruturais

### Exercício 14 — Renomeando uma coluna

A equipe decidiu que o campo:

```text
nome
```

da tabela `curso` deverá se chamar:

```text
nome_curso
```

Faça a alteração sem apagar a tabela.

**Objetivo:** praticar alteração/renomeação de coluna.

---

### Exercício 15 — Criando uma nova informação

A escola deseja armazenar o turno em que uma turma funciona.

Adicione à tabela `turma` uma coluna chamada:

```text
turno
```

Depois, altere a coluna para permitir somente valores adequados aos turnos utilizados pela escola.

**Desafio:** pense em uma maneira de restringir os valores para algo como:

```text
MANHA
TARDE
NOITE
```

---

### Exercício 16 — Removendo uma coluna

A escola decidiu que não deseja mais armazenar a carga horária diretamente na tabela `curso`.

Remova essa coluna.

**Objetivo:** praticar `ALTER TABLE ... DROP COLUMN`.

**Atenção:** antes de executar, verifique se existem outras estruturas que dependem dessa coluna.

---

# Nível 6 — DROP e DELETE

### Exercício 17 — Apagando dados

Imagine que foram inseridos vários alunos de teste durante o desenvolvimento.

Remova todos os registros da tabela `aluno`, utilizando um comando de manipulação de dados.

**Pergunta:**  
Esse exercício utiliza DDL ou DML?

> Dica: o comando esperado é `DELETE`.

---

### Exercício 18 — Apagando uma tabela

Durante o desenvolvimento, foi criada por engano uma tabela chamada:

```text
teste
```

Remova essa tabela completamente.

**Objetivo:** praticar:

```sql
DROP TABLE
```

**Pergunta:**  
Qual é a diferença entre apagar os registros de uma tabela e apagar a própria tabela?

---

### Exercício 19 — Cuidado com relacionamentos

Tente remover a tabela `curso` utilizando `DROP TABLE`.

Observe o que acontece caso existam tabelas relacionadas a ela.

Explique:

1. O comando foi executado?
2. Por que o MySQL pode impedir essa operação?
3. O que aconteceria com as turmas caso o curso fosse removido?
4. Qual seria o risco de simplesmente apagar todas as tabelas sem pensar nos