# Sistema de Cadastro de Vendas - Teste de Admissão

## Descrição

Este teste técnico tem como objetivo avaliar as habilidades do candidato em resolver problemas de lógica, programação e análise de negócios. O desafio consiste na construção de um sistema de cadastro de vendas, que permite gerenciar clientes (pessoa física ou jurídica), vendas associadas a esses clientes e a seleção de planos e serviços.

## Funcionalidades

O sistema deve conter as seguintes funcionalidades principais:

1. **CRUD de Vendas**:
   - Cadastro de clientes (pessoa física ou jurídica).
   - Criação de vendas associadas aos clientes, com seleção de planos e serviços.
   - Atualização, consulta e exclusão de vendas e clientes.

2. **Dashboard de Visualização Geral**:
   - Visão geral das vendas realizadas, com possibilidade de aplicar filtros (por cliente, período, plano, etc.).
   - Deve possuir no mínimo 2 visualizações principais:
    - Média de vendas por estado (Quantidade, valor)
    - Média de planos/serviços mais vendidos
 
## Tecnologias

Você pode desenvolver a API usando uma das linguagens abaixo:
- Javascript/Typescript (Node.js com Express, AdonisJS)
- Implementação no docker (opcional)
- Front-end utilizando Javascript/Typescript (React ou VueJS)
- Banco de dados Postgres ou MongoDB

O banco de dados pode ser relacional (como PostgreSQL) ou NoSQL (como MongoDB). A escolha é livre, mas deve ser adequada à solução.

## Requisitos

### Dados a Serem Gerenciados

#### Cliente (Pessoa Física ou Jurídica)
- Nome Completo/Razão Social (obrigatório)
- CPF/CNPJ (obrigatório e validado)
- Endereço (preenchido automaticamente via API de CEP)
- Telefone (opcional)
- Email (obrigatório e validado)
- Data de Nascimento/Fundação
- Tipo: Pessoa Física ou Jurídica

#### Venda
- Cliente (obrigatório, referenciando o cadastro de cliente)
- Data da Venda
- Itens do Carrinho:
  - Plano Selecionado (Básico, Avançado, Premium)
  - Serviços Vinculados (lista de serviços com preço)
- Total da Venda
- Desconto Aplicado (se houver)

#### Planos
- Nome do Plano (Básico, Avançado, Premium)
- Descrição
- Preço Base

#### Serviços
- Nome do Serviço
- Descrição
- Preço
---
## 1. Perfil: Back-end

### Funcionalidades:

- **Desenvolvimento da API RESTful** para gerenciar os dados de clientes, vendas, planos e serviços.
- Implementação de **validações** (ex: CPF/CNPJ, e-mail, valores) e regras de negócios.
- Conectar a API a um **banco de dados** (PostgreSQL ou MongoDB).
- Implementar **filtros e paginação** nos endpoints de listagem.
- Implementar **autenticação** com JWT ou OAuth2 (opcional).
- Testes unitários e de integração para a API.

### Requisitos de Back-end:
1. **Autenticação**: Implementação de autenticação por JWT ou OAuth2 (opcional).
2. **Validação de CPF/CNPJ**: Implementar validações adequadas para CPF e CNPJ, garantindo formato correto e cálculo dos dígitos verificadores.
3. **Endereço via API**: O endereço deve ser preenchido automaticamente utilizando uma API externa (como ViaCEP).
4. **Limite de Serviços no Carrinho**: Definir um limite máximo de serviços que podem ser adicionados ao carrinho.
5. **Limite de Vendas por Cliente**: Cada cliente pode ter no máximo 10 vendas ativas.
6. **Valores diferentes de acordo com a UF**: Cada UF deverá possuir serviços/planos com valores especificos, podendo ser uma porcentagem em cima do valor base.
7. **Filtros Avançados no Dashboard**: No dashboard, implemente filtros por cliente, plano e período de tempo.

### Critérios de Avaliação

1. **Autenticação**: Implementar autenticação usando JWT ou OAuth2.
2. **Organização do Código**: A organização e estruturação do código serão avaliadas, incluindo clareza, reusabilidade e modularidade.
3. **Validação de Dados**: Verificações como a validação de CPF/CNPJ e campos obrigatórios.
4. **Estruturação do Banco de Dados**: O modelo de dados deve ser bem estruturado e refletir corretamente os relacionamentos entre entidades.
5. **Testes Unitários**: A presença de testes automatizados será considerada um diferencial.
6. **Desempenho e Escalabilidade**: O candidato deverá considerar a escalabilidade do sistema.
7. **Documentação**: O sistema deve estar bem documentado, incluindo o uso de README e docstrings no código, além de documentação para uso dos enpoints.

### Endpoints da API

#### Clientes
- `POST /clientes` - Cadastrar um novo cliente (físico ou jurídico)
- `GET /clientes` - Listar todos os clientes com paginação
- `GET /clientes/{id}` - Buscar um cliente específico
- `PUT /clientes/{id}` - Atualizar as informações de um cliente
- `DELETE /clientes/{id}` - Remover um cliente

#### Vendas
- `POST /vendas` - Registrar uma nova venda associada a um cliente
- `GET /vendas` - Listar todas as vendas com filtros opcionais (por cliente, data, etc.)
- `GET /vendas/{id}` - Buscar uma venda específica
- `PUT /vendas/{id}` - Atualizar uma venda
- `DELETE /vendas/{id}` - Cancelar uma venda

#### Planos e Serviços
- `POST /planos` - Criar um novo plano
- `GET /planos` - Listar todos os planos
- `GET /planos/{id}` - Buscar um plano específico
- `PUT /planos/{id}` - Atualizar um plano
- `DELETE /planos/{id}` - Excluir um plano
- `POST /servicos` - Criar um novo serviço
- `GET /servicos` - Listar todos os serviços
- `GET /servicos/{id}` - Buscar um serviço específico
- `PUT /servicos/{id}` - Atualizar um serviço
- `DELETE /servicos/{id}` - Excluir um serviço

#### Dashboard
- `GET /dashboard/vendas` - Exibir uma visão geral de vendas (filtros por cliente, plano, período, UF, serviços)
- `GET /dashboard/clientes` - Exibir uma visão geral de clientes cadastrados (filtros por tipo, volume de compras)

---
## 2. Perfil: Front-end

### Funcionalidades:

- Desenvolver uma **interface de usuário** que permita gerenciar clientes, vendas, planos e serviços.
- Criar uma **tela de dashboard** com filtros (cliente, plano, período, UF).
- Interface para adição/remoção de itens no carrinho de serviços.
- Validações de formulários (ex: CPF/CNPJ, e-mail).

### Requisitos de Front-end:
- Utilizar frameworks como **React.js** ou **Vue.js**.
- O front-end deve realizar as funcionalidades descritas a partir de dados mockados.
- Componentização do código e uso de padrões de arquitetura (ex: Redux/Vuex para gerenciamento de estado).
- Exibir mensagens de erro e feedback claros para o usuário.
OBS: Verificar as regras de negócio que estão na sessão de back-end. [Regras de negócio](#requisitos-de-back-end).

### Critérios de Avaliação

1. **Organização do Código**: A organização e estruturação do código serão avaliadas, incluindo clareza, reusabilidade e modularidade.
3. **Validação de Dados**: Verificações das informações de acordo com a obrigatoriedade.
4. **Testes Unitários**: A presença de testes automatizados será considerada um diferencial.
5. **Documentação**: O sistema deve estar bem documentado, incluindo o uso de README e docstrings no código, além de documentação para uso dos enpoints.
6. **Tratamento de erros**: Tratamento adequado de erros.
   
---
## 3. Perfil: Full-stack

### Funcionalidades:

- Responsável por todas as atividades descritas nos perfis de **Back-end** e **Front-end**.
- Integração completa entre as APIs e a interface de usuário.
- Implementar a lógica de **autenticação** (JWT/OAuth2) e rotas protegidas.

### Requisitos de Full-stack:
- Implementar tanto o back-end quanto o front-end, garantindo a comunicação eficiente entre ambos.
- Configurar deploy usando **Docker** (opcional).
- Implementar o dashboard com filtros de vendas e clientes.
- Garantir uma aplicação completa e funcional.

### Critérios de Avaliação

1. **Organização do Código/Projeto**: A organização e estruturação do código serão avaliadas, incluindo clareza, reusabilidade e modularidade.
3. **Integração**: Integração adequada entre back e front.
4. **Testes**: A presença de testes automatizados será considerada um diferencial.
5. **Documentação**: O sistema deve estar bem documentado, incluindo o uso de README e docstrings no código, além de documentação para uso dos enpoints.
---
## Instruções para Submissão

1. Crie um repositório público no GitHub com o código fonte.
2. Documente qualquer configuração adicional que seja necessária para rodar o sistema (ex: variáveis de ambiente, banco de dados).
3. Inclua instruções claras de como rodar a aplicação localmente, realizar as migrações no banco de dados e rodar os testes.
