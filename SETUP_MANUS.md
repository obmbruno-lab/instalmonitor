# Indústria Visual - Instalmonitor

## Visão Geral do Projeto

Sistema de monitoramento de instalações para a Indústria Visual, uma empresa de comunicação visual responsável por impressão e instalação de materiais publicitários.

### Funcionalidades Principais

- **Dashboard Administrativo**: Visão geral de jobs, métricas e relatórios
- **Dashboard do Instalador**: Interface simplificada para instaladores em campo
- **Check-in/Check-out**: Sistema de registro de início e fim de instalações com fotos
- **Gestão de Jobs**: Integração com API Holdprint para sincronização de trabalhos
- **Calendário**: Agendamento de instalações com integração Google Calendar
- **Relatórios**: Relatórios por família de produto, instalador e produtividade
- **Gestão de Usuários**: Sistema de autenticação com diferentes níveis de acesso

## Estrutura do Projeto

```
visual-clone-35/
├── backend/
│   ├── server.py          # API FastAPI principal
│   ├── init_admin.py      # Script para criar usuário admin
│   ├── requirements.txt   # Dependências Python
│   └── .env.example       # Exemplo de variáveis de ambiente
├── frontend/
│   ├── src/
│   │   ├── components/    # Componentes React reutilizáveis
│   │   ├── pages/         # Páginas da aplicação
│   │   ├── context/       # Context API (AuthContext)
│   │   ├── hooks/         # Custom hooks
│   │   └── lib/           # Utilitários
│   ├── public/            # Arquivos estáticos
│   └── package.json       # Dependências Node.js
└── tests/                 # Testes automatizados
```

## Configuração do Ambiente

### Backend (Python/FastAPI)

1. **Criar ambiente virtual e instalar dependências:**
```bash
cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

2. **Configurar variáveis de ambiente:**
```bash
cp .env.example .env
# Editar .env com suas credenciais
```

3. **Variáveis de ambiente necessárias:**
- `MONGO_URL` - URL de conexão MongoDB
- `DB_NAME` - Nome do banco de dados
- `JWT_SECRET` - Chave secreta para tokens JWT
- `HOLDPRINT_API_KEY_POA` - API Key Holdprint (Porto Alegre)
- `HOLDPRINT_API_KEY_SP` - API Key Holdprint (São Paulo)
- `GOOGLE_CLIENT_ID` - ID do cliente Google OAuth
- `GOOGLE_CLIENT_SECRET` - Secret do cliente Google OAuth
- `RESEND_API_KEY` - API Key do Resend para emails

4. **Iniciar o servidor:**
```bash
source venv/bin/activate
uvicorn server:app --host 0.0.0.0 --port 8000 --reload
```

### Frontend (React)

1. **Instalar dependências:**
```bash
cd frontend
npm install --legacy-peer-deps
```

2. **Configurar URL da API:**
Editar `src/context/AuthContext.jsx` e ajustar a `API_URL` se necessário.

3. **Iniciar o servidor de desenvolvimento:**
```bash
npm start
```

O frontend estará disponível em `http://localhost:3000`

## Tecnologias Utilizadas

### Backend
- **FastAPI** - Framework web Python
- **MongoDB** (Motor) - Banco de dados
- **JWT** - Autenticação
- **Pillow** - Processamento de imagens
- **Google APIs** - Integração com Calendar
- **Resend** - Envio de emails

### Frontend
- **React 19** - Framework UI
- **React Router** - Navegação
- **Tailwind CSS** - Estilização
- **Radix UI** - Componentes acessíveis
- **Sonner** - Notificações toast
- **Axios** - Requisições HTTP

## Páginas do Sistema

| Página | Rota | Descrição |
|--------|------|-----------|
| Login | `/login` | Autenticação de usuários |
| Dashboard | `/dashboard` | Painel principal administrativo |
| Jobs | `/jobs` | Lista de trabalhos |
| Job Detail | `/jobs/:jobId` | Detalhes de um trabalho |
| Users | `/users` | Gestão de usuários |
| Calendar | `/calendar` | Calendário de instalações |
| Check-in | `/checkin/:jobId` | Registro de início de instalação |
| Check-out | `/checkout/:checkinId` | Registro de fim de instalação |
| Checkins | `/checkins` | Lista de check-ins |
| Reports | `/reports` | Relatórios gerais |
| Metrics | `/metrics` | Métricas e KPIs |
| Profile | `/profile` | Perfil do usuário |

## API Endpoints Principais

- `POST /api/auth/login` - Autenticação
- `GET /api/jobs` - Listar trabalhos
- `GET /api/jobs/{job_id}` - Detalhes do trabalho
- `POST /api/checkins` - Criar check-in
- `PUT /api/checkins/{checkin_id}/checkout` - Realizar check-out
- `GET /api/users` - Listar usuários
- `POST /api/users` - Criar usuário
- `GET /api/reports/*` - Endpoints de relatórios

## Notas Importantes

1. O projeto requer MongoDB para funcionar
2. A integração com Holdprint API é necessária para sincronização de jobs
3. Google OAuth é opcional (para integração com Calendar)
4. Resend é usado para recuperação de senha

## Suporte

Para dúvidas sobre o projeto, entre em contato com a equipe de desenvolvimento.


---

## MongoDB Atlas - Configurado!

O cluster MongoDB Atlas foi criado e configurado para este projeto:

| Configuração | Valor |
|--------------|-------|
| **Cluster** | instalmonitor |
| **Região** | São Paulo (sa-east-1) |
| **Provedor** | AWS |
| **Plano** | Free (512 MB) |
| **Usuário DB** | bruno_db_user |

### Connection String

```
mongodb+srv://bruno_db_user:Y6YITPLc6KNQEwkY@instalmonitor.hxjinbp.mongodb.net/instalmonitor?retryWrites=true&w=majority&appName=instalmonitor
```

### Credenciais da Conta MongoDB Atlas

| Campo | Valor |
|-------|-------|
| **Email** | bruno@industriavisual.com.br |
| **Senha** | IndVisual@2025Mongo! |
| **URL** | https://cloud.mongodb.com |

### Arquivo .env do Backend (Já Configurado)

O arquivo `backend/.env` já foi criado com a connection string do MongoDB.

---

*Última atualização: 25/12/2024*
