# Projeto: Sistema de Reajuste Salarial

## 1. Objetivo

Desenvolver um sistema web para calcular o reajuste salarial dos funcionários de uma empresa, considerando o tempo de serviço, o grupo do cargo e o grau de escolaridade de cada funcionário.

O sistema deverá permitir o cadastro dos dados dos funcionários, o cálculo automático dos reajustes, a visualização dos resultados em uma tabela e a geração de relatórios sobre a folha salarial da empresa.

## 2. Regras de negócio

O reajuste salarial será calculado com base em três critérios: tempo de serviço, grupo do cargo e grau de escolaridade.

### 2.1. Percentual de reajuste por tempo de serviço

| Tempo de serviço | Reajuste |
|---|---:|
| De 0 até 5 anos | 3% |
| Acima de 5 até 10 anos | 5% |
| Acima de 10 anos | 10% |

### 2.2. Percentual de reajuste por grupo do cargo

| Grupo do cargo | Reajuste |
|---|---:|
| Grupo 1 | 2,5% |
| Grupo 2 | 4% |
| Grupo 3 | 6,5% |

### 2.3. Percentual de reajuste por escolaridade

| Grau de escolaridade | Reajuste |
|---|---:|
| Ensino fundamental | 2% |
| Ensino médio | 3% |
| Ensino superior | 5% |
| Pós-graduação | 7% |

### 2.4. Cálculo do novo salário

Os três percentuais de reajuste deverão ser calculados individualmente sobre o salário bruto atual do funcionário. Em seguida, os valores obtidos deverão ser somados ao salário original para determinar o novo salário.

**Fórmulas:**

- Reajuste por tempo de serviço = salário bruto × percentual por tempo de serviço.
- Reajuste por cargo = salário bruto × percentual do grupo do cargo.
- Reajuste por escolaridade = salário bruto × percentual de escolaridade.
- Reajuste total = soma dos três valores de reajuste.
- Novo salário = salário bruto + reajuste total.

**Exemplo:** considere um funcionário com salário bruto de R$ 3.000,00, tempo de serviço de 7 anos, cargo do Grupo 2 e ensino superior.

- Reajuste por tempo de serviço: R$ 3.000,00 × 5% = R$ 150,00.
- Reajuste por cargo: R$ 3.000,00 × 4% = R$ 120,00.
- Reajuste por escolaridade: R$ 3.000,00 × 5% = R$ 150,00.
- Reajuste total: R$ 420,00.
- Novo salário: R$ 3.420,00.

**Atenção:** os percentuais não devem ser aplicados sucessivamente sobre o salário já reajustado. Todos devem utilizar o salário bruto original como base de cálculo.

## 3. Requisitos obrigatórios

### 3.1. Formulário de entrada de dados

Desenvolva um formulário HTML para cadastrar as informações de cada funcionário. O formulário deverá conter, no mínimo, os seguintes campos:

- Nome completo do funcionário;
- Salário bruto atual;
- Tempo de serviço na empresa, em anos;
- Grupo do cargo (Grupo 1, Grupo 2 ou Grupo 3);
- Grau de escolaridade.

### 3.2. Validação com JavaScript

Utilize JavaScript para validar o preenchimento do formulário antes de realizar o cálculo. O sistema deverá:

- Impedir o envio de dados obrigatórios não preenchidos;
- Verificar se o salário informado é um número maior que zero;
- Garantir que o tempo de serviço seja um valor válido e não negativo;
- Exigir a seleção de um grupo de cargo e de um grau de escolaridade;
- Exibir mensagens claras quando houver erros de preenchimento.

### 3.3. Cálculo e exibição dos resultados

Após a validação, o sistema deverá calcular automaticamente os valores de reajuste e apresentar os resultados em uma tabela HTML.

A tabela deverá conter, no mínimo, as seguintes colunas:

- Nome do funcionário;
- Salário bruto original;
- Tempo de serviço;
- Grupo do cargo;
- Grau de escolaridade;
- Valor do reajuste por tempo de serviço;
- Valor do reajuste por cargo;
- Valor do reajuste por escolaridade;
- Valor total do reajuste;
- Novo salário.

Cada funcionário cadastrado deverá gerar uma nova linha na tabela, permitindo acompanhar o processamento dos reajustes salariais de toda a equipe.

### 3.4. Interface e aparência

Utilize o **Bootstrap** para desenvolver uma interface moderna, organizada, responsiva e visualmente agradável.

A página deverá apresentar:
- Um título para o sistema;
- Um formulário organizado e de fácil utilização;
- Botões com identificação clara;
- Uma tabela com boa legibilidade;
- Valores monetários formatados em reais (R$);
- Mensagens de sucesso e de erro quando necessário.

## 4. Funcionalidades extras

As funcionalidades a seguir deverão ser pesquisadas e implementadas como extensões do sistema.

### 4.1. Impressão da tabela

Crie um botão **“Imprimir tabela”** que permita imprimir os dados processados dos funcionários.

Pesquise como utilizar JavaScript e CSS para preparar a página para impressão, exibindo os dados da tabela de forma organizada e evitando a impressão desnecessária de elementos, como o formulário e os botões.

### 4.2. Resumo da folha salarial

Crie um botão **“Calcular folha salarial”** que apresente um resumo financeiro de todos os funcionários cadastrados.

O resumo deverá mostrar:
- Total da folha salarial antes dos reajustes;
- Valor total dos reajustes concedidos;
- Total da folha salarial após os reajustes;
- Quantidade de funcionários processados.

Os valores deverão ser calculados com base nos dados registrados na tabela, garantindo que o resumo corresponda aos funcionários cadastrados.

### 4.3. Gráficos da evolução salarial com auxílio de IA

Utilize uma ferramenta de inteligência artificial para auxiliar no planejamento ou desenvolvimento de gráficos que representem a evolução salarial dos funcionários.

Os gráficos deverão permitir comparar o salário antes e depois do reajuste. Se possível, inclua também a visualização do valor do reajuste por funcionário.

Você poderá utilizar bibliotecas JavaScript, como Chart.js, para implementar os gráficos na página.

## 5. Tecnologias obrigatórias

O projeto deverá utilizar:

- **HTML5:** estrutura da página e formulário;
- **CSS3:** ajustes visuais e personalização;
- **Bootstrap:** layout responsivo e componentes da interface;
- **JavaScript:** validação, cálculos, manipulação da tabela, relatórios e gráficos.

## 6. Critérios de avaliação

Serão considerados na avaliação:

1. Correção dos cálculos de reajuste salarial;
2. Validação adequada dos dados do formulário;
3. Inclusão correta dos funcionários na tabela;
4. Organização e qualidade da interface;
5. Uso adequado do Bootstrap;
6. Funcionamento do recurso de impressão;
7. Cálculo correto do resumo da folha salarial;
8. Implementação dos gráficos de comparação salarial;
9. Organização, legibilidade e funcionamento do código.

## 7. Entrega

Entregue os arquivos necessários para executar o projeto, com o código organizado e funcional.

As funcionalidades obrigatórias deverão estar concluídas. As funcionalidades extras deverão ser implementadas conforme as orientações do professor e apresentadas junto com o sistema.

Ao finalizar, teste o sistema com funcionários de diferentes tempos de serviço, grupos de cargo e graus de escolaridade, verificando se os valores calculados estão corretos.
