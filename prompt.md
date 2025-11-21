# PROMPT DETALHADO PARA CRIAÇÃO DO APLICATIVO TUPÃ FC - INTERFACE COMPLETA

## 1. DESCRIÇÃO COMPLETA DO APLICATIVO

### Propósito e Objetivo Principal
Criar um aplicativo web completo para o Tupã FC que funcione como plataforma centralizada de gestão esportiva, conectando administração, jogadores, staff e torcedores em uma experiência digital integrada. O aplicativo deve substituir sistemas fragmentados atuais oferecendo funcionalidades unificadas de gestão de times, calendário de jogos, sistema de ingressos, conteúdo institucional e comunidade.

### Funcionalidades Essenciais
- **Dashboard Multiusuário**: Interfaces personalizadas por perfil (Admin, Jogador, Torcedor, Staff)
- **Gestão Completa de Times**: Cadastro de elencos, escalações, estatísticas e desempenho
- **Sistema de Calendário**: Agenda unificada de jogos, treinos e eventos
- **Plataforma de Ingressos**: Venda digital com seleção de assentos e pagamento integrado
- **Portal de Conteúdo**: Notícias, galeria multimídia e comunicados oficiais
- **Área do Sócio-Torcedor**: Benefícios exclusivos, histórico e renovação de assinatura
- **Gestão Comercial**: Controle de patrocínios, parcerias e relatórios financeiros

### Público-Alvo e Personas
- **Administrador Rodrigo** (35 anos): Necessita controle total do sistema, relatórios analíticos e gestão de usuários
- **Jogadora Marina** (22 anos): Busca acompanhar seu desempenho, calendário de treinos e comunicação com staff
- **Torcedor Carlos** (45 anos): Quer comprar ingressos facilmente, acompanhar notícias e benefícios de sócio
- **Gerente Comercial Sofia** (30 anos): Precisa gerenciar patrocinadores, métricas de vendas e relatórios

### Casos de Uso Principais
1. **Gestão Completa do Clube**: Admin atualiza escalação → Sistema reflete em tempo real no aplicativo → Torcedores visualizam time atualizado
2. **Compra de Ingressos**: Torcedor seleciona jogo → Escolhe assento no mapa interativo → Realiza pagamento → Recebe QR Code digital
3. **Acompanhamento de Desempenho**: Jogador acessa suas estatísticas → Compara evolução temporal → Recebe feedback técnico
4. **Gestão Comercial**: Gerente cadastra novo patrocinador → Configura visibilidade no carrossel → Acompanha métricas de exposure

## 2. ARQUITETURA DA INTERFACE

### Estrutura de Navegação Completa

```
App Shell (Layout Principal)
├── Header Global
│   ├── Logo + Nome Clube
│   ├── Barra de Busca Global
│   ├── Notificações (badge)
│   └── Menu Usuário (Avatar + Dropdown)
├── Sidebar Navegação (responsiva)
└── Main Content Area

Rotas Principais:
/
├── /dashboard (redireciona conforme perfil)
├── /auth (login/registro)
│
├── ADMIN (/admin/*)
│   ├── /admin/overview (dashboard analytics)
│   ├── /admin/users (gestão usuários)
│   ├── /admin/teams (gestão times)
│   ├── /admin/financial (financeiro)
│   ├── /admin/content (conteúdo)
│   └── /admin/settings (configurações)
│
├── JOGADOR (/player/*)
│   ├── /player/dashboard
│   ├── /player/profile
│   ├── /player/stats
│   ├── /player/schedule
│   └── /player/messages
│
├── TORCEDOR (/fan/*)
│   ├── /fan/dashboard
│   ├── /fan/tickets (ingressos)
│   ├── /fan/store (loja)
│   ├── /fan/news (notícias)  
│   ├── /fan/membership (sócio-torcedor)
│   └── /fan/forum (comunidade)
│
├── STAFF (/staff/*)
│   ├── /staff/dashboard
│   ├── /staff/calendar (agenda)
│   ├── /staff/communication (comunicação)
│   └── /staff/documents (documentos)
│
└── PÁGINAS PÚBLICAS
    ├── /news (blog notícias)
    ├── /teams (elenco completo)
    ├── /schedule (calendário jogos)
    ├── /tickets (comprar ingressos)
    └── /about (sobre o clube)
```

### Fluxos de Usuário Detalhados

**Fluxo 1: Compra de Ingresso**
```
Página Inicial → Selecionar Jogo → Escolher Setor/Assento → 
Login/Registro → Revisar Pedido → Pagamento → Confirmação → 
QR Code no App + Email Confirmação
```

**Fluxo 2: Gestão Administrativa**
```
Login Admin → Dashboard Overview → Gestão Times → Editar Escalação → 
Publicar Alterações → Notificação Push para Usuários Afetados
```

**Fluxo 3: Acompanhamento Jogador**
```
Login Jogador → Dashboard Pessoal → Estatísticas Individuais → 
Comparar Performance → Visualizar Próximos Compromissos → 
Comunicar com Staff Técnico
```

### Estados da Aplicação

**Loading States:**
- Skeleton screens para listas e cards
- Spinners para ações específicas
- Progress bars para uploads grandes

**Error States:**
- Páginas de erro customizadas (404, 500)
- Toast notifications para erros de ação
- Fallback UI para dados indisponíveis

**Success States:**
- Confirmações visuais após ações críticas
- Animações de sucesso microinteractions
- Redirect automático após conclusões

## 3. ESPECIFICAÇÕES DE UI/UX DETALHADAS

### Sistema de Design

**Cores Primárias:**
```typescript
const colors = {
  primary: {
    50: '#f0f9ff',
    100: '#e0f2fe',
    500: '#0ea5e9', // Azul principal do clube
    600: '#0284c7',
    700: '#0369a1',
  },
  secondary: {
    500: '#f59e0b', // Amarelo complementar  
    600: '#d97706',
  },
  neutral: {
    50: '#f8fafc',
    100: '#f1f5f9',
    800: '#1e293b',
    900: '#0f172a',
  }
}
```

**Tipografia:**
```typescript
const typography = {
  fonts: {
    heading: 'Inter, system-ui, sans-serif',
    body: 'Inter, system-ui, sans-serif',
  },
  sizes: {
    xs: '0.75rem',    // 12px
    sm: '0.875rem',   // 14px  
    base: '1rem',     // 16px
    lg: '1.125rem',   // 18px
    xl: '1.25rem',    // 20px
    '2xl': '1.5rem',  // 24px
    
}
```

**Espaçamentos:**
```typescript
const spacing = {
  0: '0px',
  1: '0.25rem',    // 4px
  2: '0.5rem',     // 8px  
  3: '0.75rem',    // 12px  
  4: '1rem',       // 16px  
  6: '1.5rem',     // 24px  
}
```

### Componentes UI Específicos

#### Dashboard Cards Interativos:
```typescript
interface DashboardCardProps {
  title: string;
  value: string | number;
  change?: number; // % change positivo/negativo  
  icon?: ReactNode;
  onClick?: () => void;
  chartData?: ChartData;
}
```

#### Tabela Data Grid Avançada:
```typescript
interface DataTableProps<T> {
  data: T[];
  columns: ColumnDef<T>[];
  searchable?: boolean;
  selectable?: boolean;
  pagination?: boolean;
  onRowClick?: (row: T) => void;
}
```

#### Modal Wizard Multi-etapas:
```typescript 
interface WizardModalProps {
  steps: WizardStep[];
  currentStep: number;
  onNext: () => void;
  onBack: () => void;
  onSubmit: (data: any) => void;
}
```

#### Sistema de Notificações:
```typescript 
interface NotificationSystem {
  toast: (message: string, type?: 'success' | 'error' | 'warning') => void;
  pushNotification: (title: string, body?: string) => void;
}
```

### Padrões de Interação

**Micro-animações:**  
- Fade-in em cards ao scroll  
- Hover states com elevação suave  
- Transições entre páginas  
- Loading spinners customizados  

**Feedback Visual:**  
- Toast notifications para ações  
- Tooltips informativos  
- Estados vazios customizados  
- Confirmações destrutivas  

## 4. FUNCIONALIDADES TÉCNICAS

### Gerenciamento de Estado com Zustand

```typescript 
// stores/auth.store.ts 
interface AuthState {
user User | null;
isLoading boolean;
error string | null;

login(email string password string) Promise<void>;
logout() void;  
register(userData RegisterData) Promise<void>;
}

// stores/teams.store.ts 
interface TeamsState { teams Team[];
currentTeam Team | null; players Player[];

fetchTeams() Promise<void>;
updatePlayer(playerId string data Partial<Player>) Promise<void>;
}
```

### Validações com Zod + React Hook Form

```typescript 
// schemas/user.schemas.ts 
const loginSchema = z.object({
email z.string().email('Email inválido'),
password z.string().min(6 'Mínimo6 caracteres'),
});

const ticketPurchaseSchema = z.object({
matchId z.string().uuid(),
sectionId z.string(),
seats z.array(z.string()).min(1 'Selecione pelo menos um assento'),
paymentMethod z.enum(['credit_card' 'pix' 'boleto']),
});
```

### Integração Firebase/Firestore

```typescript 
// lib/firebase.ts - Configuração completa 
import { initializeA...