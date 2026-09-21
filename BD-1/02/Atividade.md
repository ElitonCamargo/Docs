# Avaliação de Banco de Dados

## Modelagem lógica de um sistema para Farmácia Popular

### Situação-problema

Uma Farmácia Popular pertencente ao município precisa informatizar o controle da entrega de medicamentos à população.

Atualmente, o registro das pessoas atendidas, das receitas apresentadas, dos medicamentos entregues e da movimentação do estoque é realizado manualmente. Essa forma de trabalho tem causado dificuldades para consultar informações, verificar a disponibilidade dos medicamentos e acompanhar as retiradas realizadas por cada pessoa.

Para solucionar esses problemas, a administração da farmácia solicitou o desenvolvimento de um banco de dados que permita organizar e armazenar as informações necessárias ao funcionamento do estabelecimento.

---

## Regras de negócio

Para utilizar os serviços da farmácia, cada pessoa deverá estar cadastrada no sistema. O cadastro deverá conter informações suficientes para sua identificação e contato, como:

- CPF;
- nome completo;
- data de nascimento;
- telefone;
- endereço.

Uma pessoa poderá apresentar diferentes receitas ao longo do tempo. Cada receita deverá ser registrada com:

- número ou código da receita;
- data de emissão;
- data de validade;
- nome do médico responsável;
- CRM do médico.

Uma receita pertence a apenas uma pessoa, mas uma pessoa poderá possuir nenhuma, uma ou várias receitas cadastradas.

Cada receita poderá prescrever um ou vários medicamentos. Um mesmo medicamento poderá aparecer em diferentes receitas. Para cada medicamento prescrito, deverá ser registrada a quantidade prescrita e as orientações de uso, quando existirem.

A farmácia deverá manter o cadastro dos medicamentos oferecidos à população. Deverão ser armazenadas informações como:

- código do medicamento;
- nome;
- princípio ativo;
- fabricante;
- forma farmacêutica, como comprimido, cápsula, solução ou pomada;
- dosagem ou concentração;
- quantidade disponível em estoque.

Para retirar um medicamento, a pessoa deverá apresentar uma receita válida. Durante cada retirada, o sistema deverá registrar:

- a pessoa que realizou a retirada;
- a receita apresentada;
- a data da retirada;
- os medicamentos retirados;
- a quantidade retirada de cada medicamento.

Uma única retirada poderá conter diferentes medicamentos. Além disso, uma receita poderá ser utilizada em mais de uma retirada, desde que ainda esteja dentro do prazo de validade e que a quantidade total retirada não ultrapasse a quantidade prescrita.

Uma pessoa poderá realizar diversas retiradas ao longo do tempo. Entretanto, cada retirada deverá estar relacionada a apenas uma pessoa e a uma única receita.

O estoque deverá ser atualizado sempre que ocorrer uma entrada ou uma saída de medicamento.

As entradas poderão ocorrer devido ao recebimento de novos medicamentos pela farmácia. Para cada entrada, deverão ser registrados:

- a data da entrada;
- o medicamento recebido;
- a quantidade recebida;
- o lote;
- a data de validade do lote.

As saídas ocorrerão quando os medicamentos forem entregues às pessoas. A quantidade entregue deverá ser descontada do estoque.

O sistema não deverá permitir:

- a retirada de uma quantidade superior à disponível em estoque;
- a retirada de quantidade superior à prescrita;
- a utilização de uma receita vencida;
- o registro de retirada sem uma pessoa cadastrada;
- o registro de retirada sem uma receita correspondente;
- números de CPF duplicados;
- códigos de medicamentos duplicados.

---

# Tarefa

Com base na situação-problema apresentada, desenvolva no **BRModelo** o **modelo lógico do banco de dados** para o sistema de gestão de medicamentos da Farmácia Popular.

O modelo deverá representar adequadamente todas as informações e regras de negócio descritas no enunciado.

## O diagrama deverá apresentar

1. As tabelas necessárias para o funcionamento do sistema.
2. Os atributos de cada tabela.
3. Os tipos de dados adequados para cada atributo.
4. As chaves primárias.
5. As chaves estrangeiras.
6. Os relacionamentos entre as tabelas.
7. As cardinalidades dos relacionamentos.
8. As restrições de participação, quando necessárias.
9. A resolução dos relacionamentos muitos para muitos.
10. O registro histórico das entradas e saídas de medicamentos.
11. A representação adequada das retiradas que contenham mais de um medicamento.
12. A representação adequada das receitas que prescrevam mais de um medicamento.

## Orientações importantes

- O modelo deverá ser desenvolvido na modalidade **Modelo Lógico** do BRModelo.
- Utilize nomes claros e padronizados para as tabelas e os atributos.
- Evite espaços, acentos e caracteres especiais nos nomes dos atributos.
- Escolha tipos de dados compatíveis com as informações armazenadas.
- Não utilize um único campo para armazenar vários medicamentos ou várias quantidades.
- Resolva corretamente todos os relacionamentos do tipo muitos para muitos.
- Analise as cardinalidades considerando tanto a situação atual quanto as possibilidades futuras do sistema.
- Verifique se o modelo possibilita consultar o histórico de retiradas de uma pessoa.
- Verifique se o modelo possibilita identificar os medicamentos prescritos em cada receita.
- Verifique se o modelo possibilita identificar os medicamentos entregues em cada retirada.
- Verifique se o modelo possibilita acompanhar as movimentações e a quantidade disponível em estoque.

---

# Entrega da atividade

O aluno deverá entregar:

1. Uma imagem contendo o diagrama completo e legível.
2. A entrega será realizada em: **http://atv.etec.local/bd1**

## Observação ao aluno

Não existe apenas uma forma de construir o banco de dados. Diferentes soluções poderão ser aceitas, desde que respeitem as regras de negócio, apresentem coerência e permitam o armazenamento e a consulta correta das informações solicitadas.
