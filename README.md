Estou criando uma automação em Cypress que verifica se os resultados de busca em https://blogdoagi.com.br/ estão organizados em ordem decrescente de data. 
Para isso, considerarei que após realizar uma pesquisa você pode acessar uma lista de artigos, onde cada artigo exibe a data de publicação. A automação irá:
Realizar uma busca pelo termo "valor".
Coletar a data de publicação de cada artigo.
Ordenar os artigos na página pelo resultado coletado.
Verificar se a paginação ou listagem dos artigos na página reflete essa ordenação.



 Agi/
├── cypress/                   # Diretório do Cypress para testes automatizados
│   ├── fixtures/              # Dados de teste fixos (ex: arquivos JSON)
│   ├── integration/           # Testes de integração
│   │   ├── busca_artigos.spec.js  # Teste para busca e ordenação de artigos
│   │   └── outros_testes.spec.js  # Outros testes
│   └── support/               # Comandos de suporte, scripts comuns
│       └── index.js           # Arquivo de configuração e comandos globais do Cypress
├── src/                       # Código fonte da aplicação 
│   ├── componentes/           # Componentes da aplicação
│   ├── styles/                # Arquivos de estilo
│   ├── index.js               # Ponto de entrada da aplicação
├── public/                    # Recursos públicos (HTML, imagens)
│   └── index.html             # Página HTML principal
├── tests/                     # Testes de unidade ou outros testes
│   └── example.test.js        # Testes de exemplo
├── .gitignore                 # Arquivos a serem ignorados pelo Git
├── package.json               # Dependências do projeto e scripts
├── README.md                  # Documentação do projeto
└── cypress.json               # Configurações específicas do Cypress
