# Engenharia de Requisitos — Sistema de Gestão de Farmácia

Especificação do sistema implementado em **[Drugstore-project](https://github.com/Drugstore-project)**.

Este repositório guarda o trabalho que veio *antes* do código: a elicitação das regras de negócio, a escrita das histórias de usuário e a definição dos critérios que decidem quando cada uma está pronta. O sistema foi construído depois, a partir daqui.

Disciplina de Tecnologia de Programação em Plataformas Emergentes — Universidade de Brasília.

---

## O backlog

**[`Agil/Backlog.md`](Agil/Backlog.md)** — 25 histórias de usuário em sete épicos.

Cada história traz o papel (*eu, como…*), o desejo, a justificativa (*para que eu possa…*), o requisito funcional correspondente, a prioridade em **MoSCoW** e os **critérios de aceitação**.

| Épico | Histórias | Do que trata |
|---|---|---|
| CRUD Cliente | US01–US04 | Cadastro, consulta, atualização e exclusão de clientes |
| CRUD Produto | US05–US08, US17 | Medicamentos, estoque, validade e classificação de tarja |
| Vendas | US09, US10, US18, US19 | Registro de venda, descontos e dispensação de controlados |
| Estoque | US11, US12, US20 | Alerta de estoque baixo, validade e relatórios de controlados |
| Financeiro | US13, US14 | Formas de pagamento e emissão de nota fiscal |
| Relatórios | US15, US16 | Vendas por período e movimentação de estoque |
| Permissões | US21–US25 | Papéis, escopo de ação e bloqueio de operação não autorizada |

---

## O que torna este backlog diferente de um CRUD genérico

As regras não foram inventadas: vieram da legislação que rege o setor.

**Controle sanitário (Anvisa)**
- Classificação de tarja obrigatória — isento, tarja vermelha, tarja preta — exibida em consultas e relatórios
- Venda de medicamento controlado só é confirmada mediante receita anexada e armazenada
- Bloqueio automático de venda acima da quantidade máxima permitida, com registro em log de auditoria
- Relatório de controlados separado e filtrável por tarja, com acesso restrito, para inspeção sanitária

**Proteção de dados (LGPD)**
- Exclusão de cliente com anonimização dos dados, e não remoção simples do registro
- Confirmação obrigatória antes da exclusão

**Controle de acesso**
- Papéis de vendedor, gerente e dono, com permissões configuráveis por módulo
- Vendedor não cadastra nem exclui produtos; gerente aprova desconto acima de limite; dono edita papéis
- Tentativa de ação sem permissão é bloqueada e registrada

Essas restrições são o que separa "cadastrar um produto" de "cadastrar um medicamento": mudam a modelagem de dados, o fluxo de venda e a matriz de permissões — e por isso foram definidas antes de escrever a primeira linha de código.

---

## Do requisito ao código

| Requisito daqui | Onde virou implementação |
|---|---|
| Tarja e controle de lote | `app/models/product.py`, `app/models/product_batch.py` |
| Receita para controlados | `app/models/prescription.py` |
| Papéis e permissões | `app/models/role.py`, `app/core/deps.py`, `app/crud/role_crud.py` |
| Venda e pagamento | `app/models/order.py`, `app/models/payment.py` |

Implementação completa em **[Drugstore-project](https://github.com/Drugstore-project)** — backend em FastAPI com migrations Alembic, frontend em TypeScript com testes Cypress e Selenium, orquestração em Docker e CI no GitHub Actions.

---

## Estrutura

```
Agil/
└── Backlog.md          # as 25 histórias de usuário
anotacoes/
└── aulas.md            # notas da disciplina
```
