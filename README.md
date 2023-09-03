# Loja de Computadores e Perifericos
Modelagem de banco de dados de uma loja de eletrônicos feita para um projeto da faculdade para a disciplina Gerenciamento de Dados e Informações. O projeto envolve uma equipe de seis pessoas que escolhem um tema, escolhemos o tema loja de computadores e periféricos, e a partir disso construir um minimundo, um esquemático, construção de tabelas, povoamento e consultas. Abaixo segue o minimundo da aplicação e o esquemático. Os códigos incluem a criação das tabelas, povoamento e consulta de dados em SQL.

Os integrantes da equipe são:
- Brenda Guerra
- Caio Possidio Vieira
- Caio Roberto da Silva Verçosa
- José Jovanney Silva Lima
- Monyque Lima
- Sergio Barreto



## 1. Descrição do mundo real:


A InfoHard é uma renomada empresa phygital no ramo de tecnologia, especializada na venda de computadores e periféricos de alta qualidade. Como parte do nosso ambiente profissional, precisamos armazenar informações relevantes sobre nossos usuários.
Cada usuário em nosso sistema contém os seguintes dados: e-mail, senha, nome, número(s) de telefone e idade. Além disso, também armazenamos informações sobre o endereço do usuário, incluindo rua, número, bairro, complemento e CEP. Cada usuário pode possuir um dos dois perfis: cliente ou funcionário. No entanto, uma pessoa não pode ser cliente e funcionário simultaneamente.
Quando um usuário é cadastrado como cliente, registramos uma informação adicional, que é a data de criação da conta. Por outro lado, quando um usuário é registrado como funcionário, coletamos dados como salário, data de contratação e cargo ocupado.
Cada cliente pode fazer vários pedidos, sendo que um pedido está associado a apenas um cliente, e não existem pedidos sem um cliente. Todos os pedidos possuem informações como um identificador único, a data em que foram feitos, a descrição, o preço, o status e os locais de saída e atual. Para a confirmação do pedido, é necessário verificar se ele tem um pagamento associado. Nesse caso, cada pedido possui um único pagamento, que está vinculado exclusivamente a esse pedido. No nosso banco de dados, armazenamos a data, o status, o método de pagamento e um identificador único, para uma melhor organização dos dados de pagamento.
Todo pedido deve estar associado a um ou vários produtos eletrônicos. Esses produtos possuem atributos importantes, como a quantidade disponível em estoque, o nome, o preço, a data de estoque, as características, a marca, a categoria e um identificador único.
Nossa empresa conta com transportadoras terceirizadas que realizam a entrega dos pedidos. Cada pedido só pode ser entregue por uma única transportadora. Todas as transportadoras possuem CNPJ. Além disso, informamos ao cliente a data em que o pedido foi entregue, destino, valor do frete e a data de saída.
Cada funcionário pode ser supervisionado por um único funcionário, enquanto um funcionário pode supervisionar vários outros funcionários. Além disso, um funcionário pode emitir uma ordem de serviço, que é um documento que formaliza o serviço a ser prestado para um cliente e serve como ponto de partida para a organização do trabalho. O funcionário pode emitir várias ordens de serviço, a ordem de serviço só pode ser emitida por um funcionário e toda e qualquer ordem de serviço necessita ser emitida por um funcionário. Nessa emissão, deseja-se guardar a data desta emissão. E na ordem de serviço, deseja-se guardar o protocolo, a descrição do problema e o produto para qual se deseja essa ordem de serviço.
O relacionamento "aciona" é utilizado para registrar a interação entre o cliente, o funcionário e a assistência técnica. Quando um cliente solicita assistência, é estabelecida uma ligação entre o cliente e o funcionário designado para fornecer o suporte, incluindo os detalhes específicos da assistência solicitada. Essa relação permite o acompanhamento e o gerenciamento adequado de cada solicitação de assistência técnica. O relacionamento "aciona" é essencial para garantir que nossos clientes recebam a assistência necessária de nossa equipe especializada, mantendo um registro claro e organizado de todas as interações e atividades relacionadas à assistência técnica. O cliente pode acionar uma assistência e a assistência pode ser acionada por vários clientes e por um funcionário.
A assistência técnica possui um CNPJ, uma data, uma descrição, um tipo de assistência, um status e o equipamento relacionado. Além disso, ela está associada a um protocolo de atendimento, que contém informações como a descrição do problema, as ações tomadas, as peças substituídas e os custos adicionais. A assistência pode possuir vários protocolos de atendimento mas cada protocolo só pode possuir uma assistência.
O funcionário também pode emitir uma ou várias ordens de serviço, as quais só podem ser emitidas por um único funcionário, que podem ou não resultar em um serviço que será aprovado. Uma ordem de serviço pode ser aprovada por um funcionário e um funcionário pode aprovar várias ordens de serviço. O serviço possui atributos como código da manutenção que a identifica unicamente, data de início, data de conclusão e status. Além disso, o serviço aprovado é realizado por um único funcionário, e cada funcionário trabalha em no máximo uma ordem de serviço por vez. As ordens de serviços aprovadas que possuam um custo para serem feitas maiores que R$10.000,00 reais precisam gerar relatórios. A aprovação de uma ordem de serviço gera um relatório e um relatório só é gerado por uma ordem de serviço. É desejado guardar neste relatório o código do relatório, que o identifica unicamente, e a descrição.

## 2. Objetivos da Aplicação:
Armazenamento/display dos produtos (mostrando apenas os disponíveis)
Criação de conta e armazenamento dos dados dos usuários
Login na conta
Sistema de compra, entrega e avaliação de produtos
Sistema de assistência, serviços e relatórios
Utilização de cupons para descontos nos preços

## 3. Descrição das entidades:

### 3.1 - Usuário
A entidade “Usuário” representa as pessoas que acessam de alguma forma o site, sejam elas funcionários ou clientes.

**Atributos:**
- Email (Atributo Identificador);
- Senha;
- Telefone (Multivalorado);
- Idade;
- Nome;
- Endereço (Rua, Bairro, Número, Complemento, CEP).

### 3.2 - Cliente
A entidade “Cliente” é derivada de Usuário e representa os clientes do site.

**Atributos:**
- Data de criação da conta.

### 3.3 - Funcionário
A entidade “Funcionário” é derivada de Usuário e representa os funcionários do site.

**Atributos:**
- Salário;
- Cargo;
- Data de contratação.

### 3.4 - Produto
A entidade “Produto” representa os produtos que são vendidos.

**Atributos:**
- ID_produto (atributo identificador);
- Quantidade;
- Nome;
- Preço;
- Data estoque - Data de entrada no estoque;
- Características;
- Marca;
- Categoria;

### 3.5 - Pedido
Pedido representa uma entidade, na qual o cliente faz o pedido de algum produto de loja de periféricos.

**Atributos:**
- ID_pedido - identificador do pedido (atributo identificador);
- Data;
- Descrição;
- Preço;
- Status - indica se o pedido foi confirmado, cancelado ou entregue;
- Local_saida - Local de saída da compra;
- Local_atual - Localização atual da compra.

### 3.6 - Pagamento
Pagamento representa uma entidade do pagamento de um pedido que é feito pelo cliente.

**Atributos:**
- ID_pagamento - identificador do pagamento (atributo identificador);
- Data do pagamento;
- Status - indica se efetuado o pagamento ou não;
- Método do pagamento - indica a forma como o cliente vai pagar (cartão, pix, dinheiro).

### 3.7 - Transportadora
A entidade transportadora representa a empresa que fará a entrega do pedido ao cliente.

**Atributos:**
- CNPJ (atributo identificador).

### 3.8 - Assistência
A entidade "Assistência" refere-se a um serviço solicitado pelo cliente, no qual um funcionário é acionado para fornecer a assistência necessária.

**Atributos:**
- CNPJ (atributo identificador);
- Data;
- Descrição;
- Tipo de assistência (atributo multivalorado);
- Status;
- Equipamento.

### 3.9 - Protocolo de atendimento
Protocolo de atendimento é uma entidade fraca associada a uma assistência. Ou seja, quando uma assistência é acionada, um protocolo de atendimento é gerado para esse serviço de assistência. Então o protocolo só existirá se também o atendimento.

**Atributos:**
- Código (atributo discriminador);
- Descrição do problema;
- Ações tomadas;
- Peças substituídas;
- Custos adicionais.

### 3.10 - Ordem de serviço
Essa entidade representa um serviço para um produto que é emitido pelo funcionário.

**Atributos:**
- Protocolo (atributo identificador);
- Descrição do problema;
- Produto.

### 3.11 - Aprova
Aprova é uma entidade associativa associada a funcionário e ordem de serviço. Basicamente representa que as ordens de serviço antes de serem realizadas devem passar por um sistema de aprovação por funcionários. Uma ordem de serviço pode ser aprovada por um funcionário, e um funcionário pode aprovar várias ordens de serviço.

### 3.12 - Serviço
Essa entidade representa o serviço que será feito descrito na ordem de serviço. Esse serviço será feito por um funcionário.

**Atributos:**
- Código_serviço (atributo identificador);
- Data início;
- Data de conclusão;
- Status.

### 3.13 - Relatório
Essa entidade representa os relatórios gerados pelas realizações dos serviços que tiveram um custo acima de R$10.000,00.

**Atributos:**
- Código_relatório (atributo identificador);
- Descrição.

        


## 4. Descrição dos relacionamentos:

### 4.1 - Supervisiona (Auto-relacionamento):
Auto-relacionamento com a entidade Funcionário, onde nem todo funcionário é supervisor ou supervisionado, mas que um supervisor pode supervisionar vários funcionários, mas um funcionário é supervisionado por um único supervisor.

**Cardinalidade 1:N**

### 4.2 - Faz:
Relacionamento entre Cliente e Pedido, em que um cliente pode realizar vários pedidos, e que cada pedido é realizado por no máximo um cliente. O cliente pode ou não realizar pedidos, mas cada pedido está obrigatoriamente associado a um cliente.

**Cardinalidade 1:N**

### 4.3 - Possui:
Relacionamento entre Pedido e Produto, em que um pedido obrigatoriamente está associado a produto, de forma que, cada pedido pode ter vários produtos e que cada unidade específica de produto está associada a um único pedido.

**Cardinalidade 1:N**

### 4.4 - Entrega:
Relacionamento entre Pedido e Transportadora, em que, nem todo pedido precisa ser entregue, e nem toda transportadora listada está associada a algum pedido. Mas, todo pedido que for entregue, deve ser entregue por uma única transportadora e uma transportadora pode entregar diversos pedidos.

**Atributos:**
- Destino;
- Data entrega;
- Data saída;
- Frete.

**Cardinalidade 1:N**

### 4.5 - Tem:
Relacionamento entre Pedido e Pagamento, onde nem todo pedido está associado a algum pagamento, mas quando está, se associa apenas a um único, e todo pagamento está associado a um único pedido.

**Cardinalidade 1:1**

### 4.6 - Aciona:
Relacionamento triplo entre Cliente, Funcionário e Assistência, onde toda assistência só existe se e somente se estiver associada ao relacionamento aciona. Além disso, cada funcionário associado a uma assistência pode ter vários clientes, uma assistência realizando o atendimento de um cliente é atendido por um único funcionário e um cliente sendo atendido por um funcionário está vinculado a uma única assistência.

**Cardinalidade 1:1:N**

### 4.7 - Possui:
Relacionamento entre Assistência e sua entidade fraca Protocolo de atendimento, onde nem toda assistência está associada a um protocolo de atendimento, mas todo protocolo de atendimento está associado a uma instância de assistência. E cada protocolo de atendimento está vinculado a uma única assistência, e cada assistência pode ter vários protocolos de atendimento.

**Cardinalidade 1:N**

### 4.8 - Emite:
Relacionamento entre Funcionário e Ordem de serviço, nem todo funcionário precisa emitir ordens de serviço, mas toda ordem de serviço precisa ser associada ao funcionário que a emitiu. E, um funcionário pode emitir várias ordens de serviço e uma ordem de serviço é emitida por um único funcionário.

**Atributos:**
- Data da emissão

**Cardinalidade 1:N**

### 4.9 - Aprova:
Relacionamento entre Ordem de serviço e Funcionário e também entidade associativa Serviço a ser realizado. A ordem de serviço pode ser aprovada por um único funcionário, e cada funcionário pode aprovar várias ordens de serviço. Os funcionários não têm obrigação de aprovar ordens de serviço e as ordens de serviço não precisam ser aprovadas por funcionários, pois elas podem ser negadas.

**Cardinalidade 1:N**

### 4.10 - Gera:
Relacionamento entre Relatório e a entidade associativa Aprova. Nem todo serviço a ser realizado necessita de um relatório, pois esses são gerados apenas para serviços de valores maiores que R$10.000,00. Mas todo relatório gerado deve estar associado a um serviço aprovado. Cada serviço a ser realizado necessita de no máximo um relatório, e cada relatório é único para cada serviço.

**Cardinalidade 1:1**

### 4.11 - Realiza:
Relacionamento terciário entre Funcionário, Serviço e a entidade associativa Aprova. Um serviço, que foi aprovado, é realizado por um único funcionário. Um funcionário pode, simultaneamente, realizar vários serviços aprovados, de forma que todo serviço realizado seja aprovado e realizado por funcionários. E, cada serviço realizado por um funcionário necessita ter sido aprovado.

**Cardinalidade 1:1:N**


Cardinalidade 1:1:N

## 5. Possíveis Relatórios:
- Relatório de média de contas criadas por mês;
- Relatório de média de pedidos por conta por semana (dias úteis / finais de semana);
- Relatório sobre métodos de pagamento mais utilizados;
- Relatório sobre quais equipamentos foi mais citado em acionamentos de assistência;
- Relatório de maior porcentagem de venda por tipo de produtos (categoria / marca);
- Relatório anual sobre número de contratações e quantidade de ações de atendimento (emitir ordens de serviço, gerar relatórios, realizar manutenções) executadas;


## Esquemático

Depois de construirmos o minimundo e fazermos o levantamento das entidades, atributos e relacionamentos, fizemos o esquemático da aplicação.

![Loja de computadores e periféricos-Page-1 drawio (1)](https://github.com/sergiolbarreto/Loja-de-Computadores-e-Perifericos/assets/70080558/6283601d-9faa-4f4a-85fd-87d506401702)



