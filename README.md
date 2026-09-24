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
