# Documentação do Projeto – EcoBags

## 1. Visão Geral

O EcoBags é uma solução digital desenvolvida para ajudar consumidores a gerenciar sua despensa de forma mais inteligente, saudável e sustentável. A plataforma permite registrar produtos, monitorar validades, escanear itens, avaliar sua sustentabilidade e receber alertas relevantes para apoiar decisões de consumo mais conscientes.

O projeto foi implementado como uma aplicação web moderna em React, com foco em experiência do usuário, organização de dados e integração com serviços de backend via Base44. O objetivo central é transformar a rotina de compras e armazenamento em uma experiência orientada por dados, praticidade e impacto ambiental positivo.

## 2. Objetivo do Produto

O EcoBags foi pensado para resolver desafios comuns no gerenciamento doméstico de alimentos e itens de consumo, como:

- perda de produtos por vencimento;
- baixa visibilidade sobre a composição e qualidade dos itens;
- dificuldade de comparar produtos por sustentabilidade;
- ausência de orientação prática para consumo consciente;
- baixa organização da despensa e do estoque pessoal.

A solução combina tecnologia, análise de dados e usabilidade para tornar a rotina de casa mais eficiente e alinhada com hábitos mais sustentáveis.

## 3. Público-Alvo

A plataforma atende principalmente a:

- consumidores que desejam controlar melhor sua despensa;
- usuários preocupados com saúde, nutrição e qualidade dos itens consumidos;
- pessoas interessadas em reduzir desperdício de alimentos;
- consumidores que buscam avaliar a sustentabilidade de marcas e produtos;
- usuários que valorizam uma experiência digital simples, clara e funcional.

## 4. Funcionalidades Principais

### 4.1 Gestão de Despensa
- cadastro manual de produtos;
- registro por escaneamento de código de barras ou QR Code;
- acompanhamento de quantidade, categoria e validade;
- organização por tipo de item;
- busca e filtros por marca, categoria e nome;
- visualização em cards com indicadores de sustentabilidade.

### 4.2 Escaneamento Inteligente
- leitura de códigos via câmera do usuário;
- reconhecimento automatizado de produto;
- análise de saúde, sustentabilidade e conformidade;
- sugestões de categoria e certificações;
- comparação com metas de consumo e preferências pessoais.

### 4.3 Avaliação de Marcas e Empresas
- pesquisa de marcas e fornecedores;
- avaliação de práticas relacionadas a ESG;
- análise de embalagens e impacto ambiental;
- indicador de conformidade e certificações;
- apresentação de dados sobre práticas trabalhistas e governamentais.

### 4.4 Alertas de Validade
- classificação por criticidade de vencimento;
- alertas para itens vencidos, próximos do prazo e em risco;
- painel de notificações com estatísticas;
- contagem visual de itens urgentes;
- reutilização da lógica de alertas em módulos do sistema.

### 4.5 Experiência do Usuário
- interface responsiva para mobile e desktop;
- navegação intuitiva;
- modo visual de alto contraste;
- uso de componentes reutilizáveis e design consistente;
- animações e feedback visual para maior clareza operacional.

## 5. Arquitetura da Solução

A aplicação segue uma arquitetura modular em frontend, com separação clara entre apresentação, regras de negócio e integração externa.

### 5.1 Camadas Principais

- Frontend: React + Vite
- Roteamento: React Router
- Estado e dados assíncronos: React Query
- Estilo visual: Tailwind CSS + shadcn/ui
- Animações: Framer Motion
- Autenticação e dados: Base44 SDK

### 5.2 Estrutura de Diretórios

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
│   ├── jsconfig.json.txt
│   ├── src/
│   │   ├── App.jsx.txt
│   │   ├── Layout.jsx.txt
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
└── .gitignore
```

## 6. Componentes e Módulos Principais

### 6.1 App e roteamento
O ponto de entrada da aplicação está em `ecobags/src/App.jsx.txt`. Esse módulo:

- inicializa o provedor de autenticação;
- configura o cliente de consultas reativas;
- define o roteamento principal da aplicação;
- gerencia estados globais e fallback de paginação;
- integra o componente de notificações e tracking de navegação.

### 6.2 Configuração de páginas
O arquivo `ecobags/src/pages.config.js.txt` centraliza a definição das rotas do sistema e o layout compartilhado. Isso facilita a manutenção da navegação e permite expansão simples de novas telas.

### 6.3 Autenticação
A autenticação é tratada em `ecobags/src/lib/AuthContext.jsx.txt`, responsável por:

- verificar estado de sessão;
- validar acesso do usuário;
- tratar erros de autenticação;
- direcionar o fluxo para login ou para telas de acesso restrito.

### 6.4 Alertas de validade
A lógica de alerta está em `ecobags/src/lib/pantryAlerts.js.txt`. Esse módulo calcula a criticidade dos itens com base em regras como:

- vencidos;
- vencendo hoje;
- urgência em até 3 dias;
- próximos do vencimento em até 7 dias.

Essa separação de regras melhora a reutilização da lógica e facilita atualizações futuras.

### 6.5 Integração com Base44
Os arquivos em `ecobags/src/api/` encapsulam o acesso ao backend e às entidades de dados. A estrutura ajuda a manter o código dos componentes mais limpo e focado em interface e experiência.

## 7. Tecnologias Utilizadas

### Frontend
- React 18
- Vite
- Tailwind CSS
- shadcn/ui
- Framer Motion
- React Router DOM
- React Query

### Bibliotecas de suporte
- `html5-qrcode` para leitura de códigos de barras/QR Code
- `recharts` para visualização de dados
- `react-leaflet` para mapas
- `date-fns` para manipulação de datas
- `lucide-react` para ícones
- `@hello-pangea/dnd` para drag-and-drop
- `zod` para validação de schemas
- `clsx` e `tailwind-merge` para composição dinâmica de classes

### Backend e infraestruturas
- Base44 SDK (`@base44/sdk`)
- serviços auxiliares e entidades de dados integrados ao ecossistema Base44

## 8. Fluxo de Uso

### 8.1 Login e acesso
Ao iniciar a aplicação, o sistema valida o estado de autenticação. Se o usuário estiver autenticado, o app entra no fluxo principal; se não estiver, o sistema direciona para o processo de acesso.

### 8.2 Home e dashboard
A tela inicial oferece visão geral da despensa, com dados relevantes sobre estoque, urgência de vencimento e status de sustentabilidade.

### 8.3 Escaneamento
Na página de scanner, o usuário pode:

- capturar item via câmera;
- registrar códigos manualmente;
- analisar a qualidade e a sustentabilidade do produto;
- receber recomendações e dados comparativos.

### 8.4 Despensa
A área de despensa permite organizar itens, manter controle de inventário e seguir as preferências do usuário de forma prática.

### 8.5 Notificações
A área de notificações apresenta alertas para itens próximos da validade, com classificação por prioridade e contexto de risco.

### 8.6 Marcas e ESG
A página de empresas fornece contexto de sustentabilidade, alinhamento com práticas ESG e informações relevantes para decisões de consumo consciente.

## 9. Requisitos de Execução

### Requisitos técnicos
- Node.js 18+
- npm ou yarn
- navegador moderno
- acesso à internet para carregar dependências e integração Base44

### Comandos de execução

Na pasta `ecobags/`, execute:

```bash
npm install
npm run dev
```

Para build de produção:

```bash
npm run build
npm run preview
```

Para validação estática:

```bash
npm run lint
```

## 10. Benefícios do Produto

O EcoBags entrega valor em múltiplas frentes:

- redução de desperdício de alimentos;
- maior organização da despensa;
- melhor visibilidade sobre alimentação e sustentabilidade;
- apoio a decisões mais alinhadas com saúde pessoal e responsabilidade ambiental;
- experiência fácil de uso, com foco em clareza e mobilidade.

## 11. Considerações de Manutenção e Evolução

O projeto foi estruturado para facilitar manutenção e expansão futura. Pontos relevantes:

- separação entre páginas, componentes e utilitários;
- modularização de regras de negócio;
- uso de camada de API para abstrair backend;
- possibilidade de evolução de módulos sem impactar o restante da interface;
- estrutura preparada para adicionar novas funcionalidades e integrações.

## 12. Pontos de Atenção

Para evoluir a solução em produção, recomenda-se:

- documentar a modelagem completa de dados persistidos;
- formalizar políticas de autenticação e autorização;
- avaliar segurança e armazenamento de informações sensíveis;
- medir performance do front-end em dispositivos móveis;
- ampliar testes automatizados de interface e regras de negócio;
- manter documentação técnica das integrações externas atualizada.

## 13. Conclusão

O EcoBags é uma solução de gestão de despensa com forte componente de sustentabilidade, saúde e organização doméstica. A combinação de tecnologias modernas, arquitetura modular e foco em UX permite uma experiência funcional, escalável e alinhada às necessidades de consumidores conscientes.

A solução demonstra potencial para evoluir em direção a um ecossistema de consumo inteligente, com expansão para novos módulos, integrações e serviços de apoio à decisão.

---

Documento elaborado para a reposição técnica e apresentação do projeto `kharapaim999-sketch/EcoBagsExten-o`.
