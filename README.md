# SysFlow

Este repositório contém a base do projeto desenvolvido para fins de treinamento. O projeto consiste no desenvolvimento de um sistema para monitoramento e simulação de
tráfego de pessoas em edifícios.

O projeto contará com as funcionalidades de cadastro e login de usuários, além de uma tela dedicada aos edifícios, onde o usuário poderá visualizar todos os edifícios que possui. 
Ao selecionar um edifício específico, será possível acessar informações detalhadas, como o fluxo de pessoas, equipamentos quebrados ou em manutenção. 
O sistema também permite o gerenciamento de câmeras, catracas, andares e elevadores, oferecendo uma visão completa da estrutura e operação de cada prédio.

### Clonando o Repositório

Para clonar esse projeto e rodar localmente, basta executar esse comando no terminal:

```
git clone --recurse-submodules https://github.com/gabrielbay011/sysflow-frontend.git
```

### Dependências Utilizadas

- **`React`**: Biblioteca JavaScript para construção de interfaces de usuário.
- **`Single-SPA`**: Framework para composição de micro front-ends.
- **`TypeScript`**: Superset de JavaScript utilizado para tipagem estática.
- **`React Router DOM`**: Gerenciamento de rotas dentro de cada micro front-end.
- **`Tailwind CSS`**: Utilitário para estilização da interface.
- **`ESLint + Prettier`**: Padronização e formatação do código.
- **`Husky`**: Ferramentas de automação para validações antes dos commits.
- **`Zod`**: Validação e definição de schemas com suporte à inferência de tipos.
- **`React Hook Form`**: Gerenciamento de formulários de forma performática e enxuta.
- **`GraphQL`**: Linguagem de consulta para APIs, utilizada em conjunto com Apollo.
- **`Apollo Client`**: Cliente GraphQL para integração com APIs e cache local.
- **`Nhost`**: Backend como serviço com autenticação, banco de dados e storage.
- **`CryptoJS`**: Biblioteca para criptografia de dados em JavaScript.

## Estrutura Geral do Projeto

### Organização dos repositórios

```
┌── 📁 sysflow-frontend/
│ ├── 📁 mfe-root-config/     # Aplicação principal que orquestra os micro front-ends
│ ├── 📁 mfe-auth/            # Micro front-end responsável pela autenticação do usuário
│ └── 📁 mfe-buildings/       # Micro front-end principal das telas de edifício
└── 📄 README.md
```

### mfe-root-config

O módulo root-config é responsável por orquestrar todos os micro front-ends da aplicação. Ele registra e carrega dinamicamente cada módulo, além de definir as rotas de acesso entre eles. Também centraliza bibliotecas compartilhadas como o `React` e `React-Dom`. Com isso, garante uma navegação fluida entre os micro front-ends.

### mfe-auth

O módulo auth é responsável por toda a autenticação da aplicação, incluindo as páginas de login e cadastro de usuários. Ambas utilizam as bibliotecas `Zod` e `React Hook Form` para garantir validações robustas e uma melhor experiência no preenchimento dos formulários. Cada página conta com seus próprios serviços dedicados à lógica de autenticação, como a verificação de credenciais no login e o envio de dados para criação de novos usuários.

### mfe-buildings

O módulo buildings é responsável por toda a gestão dos edifícios cadastrados pelo usuário. Ele exibe a lista de edifícios pertencentes ao usuário e permite o acesso a informações detalhadas de cada um. Entre os dados disponíveis estão o fluxo de pessoas, equipamentos quebrados ou em manutenção, além de detalhes sobre câmeras, catracas, elevadores e andares. 
### Estrutura de Cada Micro Front-End

```
📁 [nome-do-módulo]/
├── 📁 src/
│   ├── 📁 [nome-da-página]/
│   │   ├── 📁 components/
│   │   │   └── 📄 [arquivo-componente].tsx
│   │   ├── 📁 services/
│   │   │   └── 📄 [arquivo-service].ts
│   │   ├── 📁 types/
│   │   │   └── 📄 [arquivo-type].ts
│   │   ├── 📁 schemas/
│   │   │   └── 📄 [arquivo-schema].ts
│   │   ├── 📁 validators/
│   │   │   └── 📄 [arquivo-validator].ts
│   │   └── 📁 Pages/
│   │       └── 📄 [arquivo-página].tsx
│   │
│   ├── 📁 utils/
│   │   ├── 📁 components/
│   │   │   └── 📄 [arquivo-componente].tsx
│   │   ├── 📁 services/
│   │   │   └── 📄 [arquivo-service].ts
│   │   ├── 📁 types/
│   │   │   └── 📄 [arquivo-type].ts
│   │   └── 📁 validators/
│   │       └── 📄 [arquivo-validator].ts
│   │
│   ├── 📄 [nome-do-módulo].tsx     # Adapta o micro front-end react para o single-spa
│   ├── 📄 root.component.tsx       # Componente que define as rotas da aplicação
│   ├── 📄 index.css                # Estilos globais via Tailwind CSS
│   └── 📄 declarations.d.ts        # Tipagens globais para arquivos estáticos
│   
├── 📄 .eslintrc
├── 📄 .gitignore
├── 📄 .prettierignore
├── 📄 .prettierrc
├── 📄 babel.config.json
├── 📄 jest.config.js
├── 📄 package-look.json
├── 📄 package.json
├── 📄 postcss.config.js
├── 📄 tsconfig.json
├── 📄 webpack.config.js
└── 📄 README.md
```

## Configurações Gerais de React e Single-SPA

- Todos os micro front-ends são aplicações React, registradas no root-config via registerApplication.
- O root-config é responsável por carregar dinamicamente os módulos via SystemJS, mantendo a separação entre contextos (cada micro front-end).
- O React Router Dom é utilizado dentro de cada micro front-end para gerenciamento interno de rotas.

## Convenções de Codificação

- Estrutura modular: Cada funcionalidade deve ser organizada em pastas separadas (pages, components, services, etc.).
- Nomenclatura: Seguir a convenção `camelCase` para variáveis e funções, `PascalCase` para componentes e classes.
- Validações com Zod integradas ao React Hook Form.
- Código reutilizável isolado na pasta `utils`.

## Padrão de Versionamento

### Branches por Task

- As branches dos repositórios seguem um padrão onde cada uma delas representa uma nova funcionalidade ou melhoria.

### Commits

- Cada commit representa uma mudança significativa no código, iniciando com o tipo da mudança e depois uma pequena descrição do que foi alterado ou implementado.

## Fluxo de Desenvolvimento

1. Criar uma branch a partir de `main` para cada nova funcionalidade.
2. Desenvolver a funcionalidade em conformidade com os padrões de codificação.
3. Comitar alterações seguindo a convenção semântica de commits.
4. Submeter o código para a branch de dev via pull request.
5. Após aprovação, realizar o merge com a `main`.

## Equipe
| Nome           | Stack               |                                  
| -------------- | ------------------- |
| Mike Will      | Front-end           |
| Gabriel        | Back-end            |
