# ClinNext (SaaSClinico)

SaaS completo de gestão para clínicas, do backend à interface. Desenvolvido para substituir planilhas e sistemas fragmentados por um fluxo único: agendamento, prontuário, frequência, mensalidades e relatórios, com isolamento de dados por clínica.

## Stack

- **Backend:** Flask (Python 3.11) + Supabase
- **Frontend:** Next.js 14 + TypeScript + Tailwind CSS
- **Banco:** PostgreSQL (Supabase), com Row Level Security
- **Auth:** Supabase Auth + JWT

## Principais funcionalidades

- Multi-tenant com isolamento por clínica (aplicação + RLS no banco)
- Agendamentos com validação de conflito de horário
- Prontuários com controle de acesso por papel (admin, recepção, profissional)
- Controle de frequência e mensalidades
- Upload e geração de relatórios (PDF)
- Dashboard com métricas da clínica

## Papéis e permissões

| Papel | Pacientes | Agendamentos | Prontuários | Relatórios |
|---|---|---|---|---|
| admin | CRUD | CRUD | CRUD | CRUD |
| recepção | CRUD | CRUD | Ver | Ver |
| profissional (fono/médico) | Ver | Ver | CRUD próprios | CRUD próprios |

## Estrutura do projeto

```
backend/            API Flask (routes, services, repositories)
frontend-next/       Aplicação Next.js
supabase/            Migrations e RPC functions do banco
docs/                Documentação complementar
loadtest/            Scripts de teste de carga
```

## Documentação

- [RESUMO_ARQUITETURA.md](RESUMO_ARQUITETURA.md) — visão geral rápida de endpoints, fluxo de auth e estrutura
- [ARQUITETURA_TECNICA.md](ARQUITETURA_TECNICA.md) — documentação técnica completa
- [GUIA_PRATICO_API.md](GUIA_PRATICO_API.md) — guia de uso da API
- [PLANO_EVOLUCAO.md](PLANO_EVOLUCAO.md) — roadmap de evolução do produto

## Rodando localmente

```bash
# Backend
cd backend
python -m venv venv
venv\Scripts\activate  # Windows
pip install -r requirements.txt
python -c "from app import create_app; app = create_app(); app.run()"

# Frontend (em outro terminal)
cd frontend-next
npm install
npm run dev
```

Projeto relacionado: [landing page de vendas](https://github.com/AndersonGabrielBD/ladinpageclinnext)
