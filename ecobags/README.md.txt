# 🌿 EcoBags

Aplicativo de gestão inteligente de despensa com foco em sustentabilidade, saúde e impacto ecológico. Escaneie produtos, avalie marcas, acompanhe validades e tome decisões de consumo mais conscientes.

---

## ✨ Funcionalidades Principais

### 📦 Gestão de Despensa
- Cadastro manual e por escaneamento de produtos
- Acompanhamento de quantidade, categoria e data de validade
- Filtros por categoria e busca por nome/marca
- Cards visuais com indicadores de sustentabilidade

### 📸 Escaneamento Inteligente
- Leitura de códigos de barras e QR codes via câmera (`html5-qrcode`)
- Avaliação automática de produtos com IA (saúde, sustentabilidade, conformidade)
- Entrada manual com sugestões de categoria e certificações
- Análise nutricional comparada a metas diárias do usuário

### 🏢 Avaliação de Empresas
- Pesquisa de marcas com IA (ESG, práticas trabalhistas, embalagens)
- Pontuações de embalagem, práticas da empresa e avaliação de funcionários
- Status de conformidade governamental
- Certificações e alertas de alérgenos

### 🔔 Alertas de Validade
- Classificação por criticidade: vencido, hoje, urgente (≤3 dias), em breve (≤7 dias)
- Painel de estatísticas na página de notificações
- Badge no menu com contagem de produtos expirando
- Motor de alertas funcional e reutilizável (`src/lib/pantryAlerts.js`)

### 🎨 Interface
- Design "Tech-First" com modo escuro de alto contraste
- Layout responsivo (mobile + desktop)
- Navegação inferior no mobile, barra superior no desktop
- Animações com Framer Motion

---

## 🛠️ Stack Tecnológica

| Camada | Tecnologia |
|--------|-----------|
| Frontend | React 18 + Vite |
| Estilo | Tailwind CSS + shadcn/ui |
| Animações | Framer Motion |
| Ícones | lucide-react |
| Gráficos | Recharts |
| Mapas | react-leaflet |
| Arrastar e soltar | @hello-pangea/dnd |
| Scanner | html5-qrcode |
| Datas | date-fns |
| Backend/Auth/DB | Base44 (BaaS) |

---

## 📁 Estrutura do Projeto

```
src/
├── pages/              # Páginas da aplicação
│   ├── Home.jsx        # Dashboard inicial com métricas
│   ├── Scanner.jsx     # Escaneamento e avaliação de produtos
│   ├── Pantry.jsx      # Gestão da despensa
│   ├── Notifications.jsx # Alertas de validade
│   ├── Companies.jsx   # Avaliação de empresas
│   ├── Profile.jsx     # Perfil e preferências do usuário
│   ├── About.jsx       # Sobre o app
│   └── Welcome.jsx     # Tela de boas-vindas
├── components/
│   ├── scanner/        # Componentes de escaneamento
│   ├── pantry/         # Cards e formulários da despensa
│   ├── companies/      # Avaliação de empresas
│   ├── nutrition/      # Análise nutricional
│   └── ui/             # Componentes shadcn/ui
├── lib/
│   ├── pantryAlerts.js # Motor de alertas (composição funcional)
│   ├── AuthContext.jsx # Contexto de autenticação
│   └── utils.js        # Utilitários (cn, etc.)
└── api/
    ├── base44Client.js # Cliente Base44 SDK
    ├── entities.js     # Wrappers de entidades
    └── integrations.js # Wrappers de integrações
```

---

## 🚀 Como Executar Localmente

```bash
# Instalar dependências
npm install

# Iniciar servidor de desenvolvimento
npm run dev

# Build de produção
npm run build

# Pré-visualizar build
npm run preview
```

---

## 🗃️ Modelo de Dados

### PantryItem
Armazena os produtos da despensa do usuário.

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `product_name` | string | Nome do produto (obrigatório) |
| `brand` | string | Marca/fabricante (obrigatório) |
| `barcode` | string | Código de barras (se escaneado) |
| `category` | enum | food, beverage, personal_care, household, other |
| `expiration_date` | date | Data de validade |
| `quantity` | number | Quantidade em estoque |
| `image_url` | string | URL da imagem do produto |
| `sustainability_score` | number | Pontuação de sustentabilidade (0-100) |
| `matches_preferences` | boolean | Se atende às preferências do usuário |
| `evaluation_data` | object | Avaliação detalhada (embalagem, práticas, conformidade, alérgenos, certificações) |
| `notes` | string | Observações do usuário |

---

## 🔐 Autenticação

A autenticação é gerenciada pelo Base44 (backend-as-a-service). Os usuários acessam o app via convite e login. Não há lógica de auth no frontend além do consumo do contexto.

---

## 🌱 Sustentabilidade

O EcoBags avalia produtos em três dimensões:

1. **Embalagem** — reciclabilidade e impacto ambiental
2. **Práticas da empresa** — ESG, cadeia de suprimentos, ética
3. **Avaliação de funcionários** — satisfação e condições de trabalho

Cada produto recebe uma pontuação de sustentabilidade (0-100) exibida visualmente nos cards.

---

## 📱 Publicação

O app está publicado e acessível via Base44. O mesmo código-base gera builds nativos para iOS e Android.

---

## 📄 Licença

Projeto privado. Todos os direitos reservados.