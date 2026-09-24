# Documentação do Projeto EcoBags

## Visão Geral

O EcoBags é uma aplicação web para gestão de despensa e consumo consciente, com foco em sustentabilidade, saúde e impacto ambiental. O sistema permite:

- registrar produtos na despensa;
- escanear códigos de barras e QR Codes;
- avaliar a sustentabilidade de marcas e produtos;
- monitorar validades e alertas de vencimento;
- comparar produtos com preferências pessoais;
- acompanhar empresas e práticas ESG.

A aplicação foi construída em React com Vite e integra serviços do Base44 para autenticação, dados e backend sem a necessidade de uma infraestrutura customizada.

## Repositório

- Nome: `EcoBagsExten-o`
- Organização: `kharapaim999-sketch`
- Diretório principal do app: `ecobags/`

## Stack Tecnológica

### Frontend
- React 18
- Vite
- Tailwind CSS
- shadcn/ui
- Framer Motion
- React Router
- React Query

### Bibliotecas e utilitários
- `html5-qrcode` para leitura de códigos
- `recharts` para gráficos
- `react-leaflet` para mapas
- `date-fns` para manipulação de datas
- `lucide-react` para ícones
- `@hello-pangea/dnd` para arrastar e soltar
- `zod` para validação
- `clsx` + `tailwind-merge` para classes utilitárias

### Backend / Infraestrutura
- Base44 SDK (`@base44/sdk`)
- Integração com serviços e entidades do Base44

## Estrutura do Projeto

```text
EcoBagsExten-o/
├── README.md
├── DOCUMENTACAO.md
├── ecobags/
│   ├── README.md.txt
│   ├── package.json.txt
│   ├── vite.config.js.txt
│   ├── tailwind.config.js.txt
│   ├── eslint.config.js.txt
│   ├── index.html.txt
│   ├── jsconfig.json.txt
│   ├── components.json.txt
│   ├── postcss.config.js.txt
│   ├── src/
│   │   ├── App.css.txt
│   │   ├── App.jsx.txt
│   │   ├── Layout.jsx.txt
│   │   ├── index.css.txt
│   │   ├── main.jsx.txt
│   │   ├── pages.config.js.txt
│   │   ├── api/
│   │   │   ├── base44Client.js.txt
│   │   │   ├── entities.js.txt
│   │   │   └── integrations.js.txt
│   │   ├── components/
│   │   ├── hooks/
│   │   │   └── use-mobile.jsx.txt
│   │   ├── lib/
│   │   │   ├── AuthContext.jsx.txt
│   │   │   ├── NavigationTracker.jsx.txt
│   │   │   ├── PageNotFound.jsx.txt
│   │   │   ├── VisualEditAgent.jsx.txt
│   │   │   ├── app-params.js.txt
│   │   │   ├── pantryAlerts.js.txt
│   │   │   ├── query-client.js.txt
│   │   │   └── utils.js.txt
│   │   ├── pages/
│   │   │   ├── About.jsx.txt
│   │   │   ├── Companies.jsx.txt
│   │   │   ├── Home.jsx.txt
│   │   │   ├── Notifications.jsx.txt
│   │   │   ├── OAuthConsent.jsx.txt
│   │   │   ├── Pantry.jsx.txt
│   │   │   ├── Profile.jsx.txt
│   │   │   ├── Scanner.jsx.txt
│   │   │   └── Welcome.jsx.txt
│   │   └── utils/
│   └── base44/
│       └── ...
└── .gitignore
```

## Arquitetura da Aplicação

### 1. Estrutura principal

A aplicação inicia em `ecobags/src/App.jsx.txt`:

- envolve a aplicação com `AuthProvider`;
- inclui o `QueryClientProvider` do React Query;
- configura o roteamento com `react-router-dom`;
- renderiza a navegação e o sistema de notificações global;
- define as rotas principais.

### 2. Configuração de páginas

A definição de páginas está em `ecobags/src/pages.config.js.txt`.

O objeto `pagesConfig` determina:

- página principal (`mainPage`);
- mapeamento de rotas e componentes (`Pages`);
- layout compartilhado (`Layout`).

As páginas são organizadas em `src/pages/` e incluem:

- `Home` — dashboard inicial
- `Scanner` — escaneamento de produtos
- `Pantry` — gestão da despensa
- `Notifications` — alertas de validade
- `Companies` — avaliação de empresas
- `Profile` — perfil do usuário
- `About` — informações do aplicativo
- `Welcome` — tela de boas-vindas

### 3. Camada de autenticação

A autenticação é tratada em `ecobags/src/lib/AuthContext.jsx.txt`.

Este módulo:

- verifica o estado de autenticação;
- gerencia login e redirecionamento;
- trata erros de usuário não registrado;
- integra com a infraestrutura Base44.

### 4. Lógica de alertas de despensa

A lógica de alertas e priorização de vencimentos fica em `ecobags/src/lib/pantryAlerts.js.txt`.

Esse módulo é responsável por:

- classificar produtos por criticidade;
- calcular urgência por data de validade;
- gerar alertas e contadores visuais;
- suportar a tela de notificações.

### 5. Integração com dados

A pasta `ecobags/src/api/` reúne wrappers para acesso ao Base44:

- `base44Client.js.txt` — cliente principal
- `entities.js.txt` — abstrações de entidades
- `integrations.js.txt` — integrações específicas

Essas camadas centralizam o acesso a dados e minimizam acoplamento dos componentes com a infraestrutura.

## Fluxo de uso principal

### 1. Login e autenticação

Ao abrir a aplicação, o `App` monta o `AuthProvider` e valida o estado do usuário. Em caso de não cadastro, a aplicação mostra uma tela específica de erro; em caso de sessão inválida, ela redireciona para login.

### 2. Dashboard

A rota inicial `Home` apresenta uma visão geral com KPIs e métricas de despensa, sustentabilidade e alertas.

### 3. Escaneamento

Na página `Scanner`, o usuário pode:

- usar a câmera para ler códigos de barras ou QR Codes;
- registrar um produto manualmente;
- avaliar saúde, sustentabilidade e conformidade;
- receber sugestões baseadas na categoria e preferências.

### 4. Gestão da despensa

A página `Pantry` permite:

- adicionar/editar produtos;
- filtrar por categoria;
- consultar quantidade e validade;
- visualizar indicadores de impacto ecológico.

### 5. Alertas e notificações

A tela `Notifications` usa o motor de alertas para:

- classificar itens próximos do vencimento;
- exibir status crítico, urgente e em breve;
- mostrar contagens no menu.

### 6. Empresas e ESG

A área `Companies` fornece informação sobre marcas e práticas ambientais, sociais e de governança.

## Principais funcionalidades

### Gestão de despensa
- cadastro manual e por escaneamento;
- acompanhamento de categorias e quantidades;
- busca e filtros;
- indicadores de sustentabilidade.

### Escaneamento inteligente
- leitura de códigos via câmera;
- avaliação com IA;
- análise nutricional e comparação com metas do usuário;
- sugestão de categoria e certificações.

### Avaliação de empresas
- pesquisa de marcas;
- pontuação ESG;
- conformidade governamental;
- alertas de alérgenos e certificações.

### Sustentabilidade
- avaliação de embalagem;
- práticas de cadeia de suprimentos;
- impacto de produção e consumo.

## Comandos de Desenvolvimento

Na pasta `ecobags/`:

```bash
npm install
npm run dev
npm run build
npm run preview
npm run lint
```

## Observações sobre o projeto

- O app é uma aplicação frontend moderna, com foco em UX e visualização de informações;
- o backend é abstraído por Base44, reduzindo a necessidade de implementação de API manual;
- há forte presença de componentes de UI reutilizáveis, páginas modulares e regras de negócio isoladas em módulos auxiliares;
- o projeto combina funcionalidade de consumo consciente com uma interface de alto contraste e visual "tech-first".

## Melhorias sugeridas para documentação futura

- incluir diagramas de fluxo de autenticação;
- detalhar cada página da aplicação com exemplos de uso;
- documentar os modelos de dados do produto;
- registrar a integração com o Base44 e as entidades persistidas;
- incluir convenções de nomenclatura e padrões de contribuição.

## Conclusão

O EcoBags é um aplicativo de gestão de consumo consciente e despensa sustentável, com arquitetura moderna em React/Vite, integração com Base44 e foco em experiência de usuário. A estrutura do projeto está organizada em páginas, componentes reutilizáveis, utilitários e módulos de integração, permitindo manutenção e evolução com baixo acoplamento.

---

Documentação gerada para o repositório `kharapaim999-sketch/EcoBagsExten-o`.
