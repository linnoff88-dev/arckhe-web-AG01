# INEMA.Club

Plataforma educacional focada em **Inteligencia Artificial** e **Robotica**. Preparamos voce para as profissoes do futuro com metodologia pratica, jogos educativos e comunidade ativa.

## Sobre o Projeto

O INEMA.Club e uma plataforma que oferece:

- **Aprendizado Acelerado** - Metodologia que combina teoria e pratica
- **Jogos Educativos (EAI)** - Aprenda IA de forma divertida em eai.inema.club
- **Comunidade INEMA.VIP** - Networking e troca de experiencias no Telegram
- **Mentorias Exclusivas** - Acompanhamento personalizado com especialistas
- **Certificados** - Reconhecimento oficial de conclusao

## Funcionalidades do Site

| Funcionalidade | Status | Descricao |
|----------------|--------|-----------|
| Landing Page | Ativo | Apresentacao completa da plataforma |
| Diagnostico IA | Demo | Analise de potencial com IA (mockado) |
| Login/Dashboard | Desativado | Requer configuracao do Supabase |
| Planos/Precos | Ativo | Basico (Gratis), Premium (R$97), VIP (R$297) |

## Modo Demo vs Producao

O site esta configurado em **modo demo** para funcionar sem dependencias externas.

### Modo Demo (Atual)
- Site funciona 100% sem configuracao
- Diagnostico IA retorna dados de exemplo
- Login/Dashboard desativados
- Bundle otimizado: ~373KB

### Modo Producao (Requer Configuracao)
Para ativar todas as funcionalidades, configure as variaveis de ambiente:

| Variavel | Servico | Funcionalidade |
|----------|---------|----------------|
| `VITE_GEMINI_API_KEY` | Google AI | Diagnostico com IA real |
| `VITE_SUPABASE_URL` | Supabase | Login e Dashboard |
| `VITE_SUPABASE_ANON_KEY` | Supabase | Login e Dashboard |

## Executar Localmente

**Requisitos:** Node.js 16+

```bash
# Clonar repositorio
git clone https://github.com/inematds/web-AG01.git
cd web-AG01

# Instalar dependencias
npm install

# Executar em desenvolvimento
npm run dev

# Build para producao
npm run build
```

O site estara disponivel em `http://localhost:3000`

## Deploy no Vercel

1. Acesse [vercel.com](https://vercel.com)
2. Importe o repositorio `inematds/web-AG01`
3. Deploy automatico (funciona sem variaveis de ambiente)
4. (Opcional) Adicione variaveis para funcionalidades extras

**URL de Producao:** https://web-ag01.vercel.app/

## Ativar Funcionalidades Extras

### Diagnostico com IA Real (Google Gemini)

1. Acesse [Google AI Studio](https://aistudio.google.com/)
2. Crie uma API Key
3. No Vercel: Settings > Environment Variables
4. Adicione: `VITE_GEMINI_API_KEY` = sua_chave
5. Edite `services/geminiService.ts` e descomente o codigo original

### Login e Dashboard (Supabase)

1. Crie conta em [supabase.com](https://supabase.com)
2. Crie um novo projeto
3. Execute o SQL abaixo no SQL Editor:

```sql
-- Tabela de usuarios
CREATE TABLE users (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  password TEXT NOT NULL,
  name TEXT NOT NULL,
  website TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Tabela de dashboard
CREATE TABLE user_dashboard (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  goal TEXT,
  income NUMERIC,
  clients INTEGER,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Habilitar RLS
ALTER TABLE users ENABLE ROW LEVEL SECURITY;
ALTER TABLE user_dashboard ENABLE ROW LEVEL SECURITY;

-- Politicas de acesso
CREATE POLICY "Allow all" ON users FOR ALL USING (true);
CREATE POLICY "Allow all" ON user_dashboard FOR ALL USING (true);
```

4. Copie a URL e Anon Key do projeto
5. No Vercel, adicione:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_ANON_KEY`

## Estrutura do Projeto

```
web-AG01/
â”œâ”€â”€ components/          # Componentes React
â”‚   â”œâ”€â”€ Navbar.tsx       # Navegacao
â”‚   â”œâ”€â”€ Hero.tsx         # Secao principal
â”‚   â”œâ”€â”€ Features.tsx     # Metodologia INEMA
â”‚   â”œâ”€â”€ Pricing.tsx      # Planos e precos
â”‚   â”œâ”€â”€ Testimonials.tsx # Depoimentos
â”‚   â”œâ”€â”€ AuditTool.tsx    # Diagnostico IA
â”‚   â”œâ”€â”€ AuthForm.tsx     # Login/Cadastro
â”‚   â”œâ”€â”€ Dashboard.tsx    # Painel do usuario
â”‚   â””â”€â”€ Footer.tsx       # Rodape
â”œâ”€â”€ services/
â”‚   â””â”€â”€ geminiService.ts # Integracao Google AI (demo)
â”œâ”€â”€ lib/
â”‚   â””â”€â”€ supabase.ts      # Cliente Supabase (opcional)
â”œâ”€â”€ App.tsx              # Componente principal
â”œâ”€â”€ index.tsx            # Entrada da aplicacao
â””â”€â”€ index.html           # HTML base
```

## Stack Tecnologica

- **React 19** - Framework UI
- **TypeScript** - Tipagem estatica
- **Vite** - Build tool rapido
- **Tailwind CSS** - Estilizacao
- **Framer Motion** - Animacoes
- **Lucide React** - Icones
- **Supabase** - Backend (opcional)
- **Google Gemini** - IA (opcional)
- **Vercel** - Hospedagem

## Links Uteis

- **Site:** https://web-ag01.vercel.app/
- **EAI Games:** https://eai.inema.club
- **INEMA.VIP:** Comunidade no Telegram
- **Repositorio:** https://github.com/inematds/web-AG01

## Contribuicao

1. Fork o repositorio
2. Crie uma branch: `git checkout -b minha-feature`
3. Commit: `git commit -m "Adiciona feature"`
4. Push: `git push origin minha-feature`
5. Abra um Pull Request

## Licenca

MIT

---

Feito com dedicacao para o futuro da educacao em IA e Robotica.

---

Projeto  - ARCKHÉe