# Help Desk com Sistema de Tickets

API REST de suporte com papéis (cliente/agente), fluxo de tickets e métricas de atendimento.

> 📦 **Template de trabalho em grupo da WebForge.** Clique em **Use this template** (botão verde acima) para criar o repositório do seu grupo.

## 🚀 Como rodar

```bash
npm install
npm start        # inicia em http://localhost:3007
```

O projeto já sobe com uma rota raiz `GET /`. Todo o resto é com o grupo.

## 📋 Requisitos

- **Auth/Papéis** — registro com papel (cliente ou agente), login JWT e middleware de autorização por papel.
- **Tickets** — abrir chamado (cliente); listar (cliente vê os próprios, agente vê todos, com filtros); alterar status e atribuir a agente (agente).
- **Comentários** — adicionar e listar comentários do ticket em ordem cronológica.
- **Métricas** — tempo médio de resolução, tickets por agente e distribuição por status.

> Persistam os dados (arquivo JSON ou SQLite) — os testes podem reiniciar o servidor entre etapas.

## ✅ O que os testes de correção validam

Os testes automáticos sobem o **seu** servidor e fazem requisições HTTP reais contra a API. Eles verificam **comportamento** (status HTTP e corpo das respostas), não a estrutura interna do código — organizem os arquivos como preferirem. Para ser aprovado, a API precisa:

- [ ] `GET /` responde **200**.
- [ ] `POST /auth/registro` aceita o papel (cliente/agente) e `POST /auth/login` retorna JWT.
- [ ] Um cliente **não** consegue ver tickets de outro cliente (**403**).
- [ ] Um agente lista **todos** os tickets.
- [ ] Transição de status inválida (ex.: aberto → fechado direto) responde **400** ou **409**.
- [ ] Um **cliente** que tenta alterar status ou atribuir ticket recebe **403**.
- [ ] `GET /metricas/tempo-resolucao` retorna o tempo médio entre abertura e resolução.

## 👥 Trabalho em equipe (obrigatório)

Este é um ambiente o mais próximo possível do mercado:

- O repositório deve pertencer a **um** dos membros do grupo. Os **demais membros entram como colaboradores** em `Settings → Collaborators → Add people`.
- Cada membro trabalha em sua **própria branch** e abre **Pull Request** para a `main`, pedindo revisão de outro colega.
- A WebForge mede as **contribuições individuais** de cada membro (commits, linhas adicionadas e removidas) direto do histórico do GitHub. Distribuam bem o trabalho.

## 🧱 Stack

- Node.js + Express (CommonJS)
