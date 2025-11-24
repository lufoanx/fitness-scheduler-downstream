# Blueprint do Downstream — Fitness Scheduler API

## 1. Contexto do Projeto
A Fitness Scheduler API é uma API simples para organizar treinos do usuário, permitindo criar, editar, listar e concluir treinos.  
Mesmo sendo um sistema pequeno, o objetivo aqui é mostrar como o time cuidaria da parte de qualidade, organização e entrega usando práticas de downstream, conforme a Unidade 3 da disciplina.

A ideia é deixar claro como vamos trabalhar: como usamos Git, como garantimos qualidade do código, como o pipeline funciona, como testamos e como colocamos algo em produção de forma segura.

---

## 2. Git, Branches, PR e DoD
### Branches
Usamos um modelo simples e curto, para evitar acúmulo de mudanças:

- `feat/nova-funcionalidade`
- `fix/ajuste`
- `chore/tarefa-interna`

As branches são pequenas e sempre voltam rápido para a `main`.

### Commits
Adotamos um padrão básico inspirado em *Conventional Commits*, para manter organização:

- `feat:` quando cria algo novo  
- `fix:` correção  
- `test:` testes  
- `docs:` documentação  
- `refactor:` melhorias internas  

### Pull Requests
Todo PR deve ter:
- descrição do que foi feito  
- motivo da mudança  
- checklist do DoD  
- status da pipeline  
- quem revisou  

### Definition of Ready (DoR)
Uma tarefa só entra no desenvolvimento quando:
- critérios de aceitação estão claros  
- dependências foram verificadas  
- impacto foi discutido  
- dados de teste estão definidos  

### Definition of Done (DoD)
Uma tarefa só termina quando:
- PR aprovado  
- testes passando  
- cobertura acima de 70%  
- lint sem erros  
- SAST sem alertas críticos  
- alterações documentadas se necessário  

---

## 3. Qualidade e Testes
A pirâmide de testes será assim:

- **Unitários (maior parte):** funções básicas, validações, regras simples  
- **Integração:** verificar rotas e interação com o banco  
- **E2E (poucos):** fluxo completo “criar treino → listar → concluir”

Meta de cobertura: **70%**, sendo uma cobertura útil, não feita só para os números.

### Ferramentas
- Lint: ESLint  
- SAST: CodeQL ou Semgrep (falha se houver HIGH/CRITICAL)  

---

## 4. Pipeline CI/CD e Ambientes
O pipeline mínimo será:

1. Instalar dependências  
2. Rodar lint  
3. Rodar testes  
4. Conferir cobertura  
5. Rodar SAST  
6. Gerar artefato/build  

### Ambientes
**dev**  
- logs mais detalhados  
- dados fictícios  
- testes locais  

**staging**  
- espelho da produção  
- validação completa da release  
- teste de migrações e rotas  

**produção**  
- só recebe deploy pelo pipeline  
- artefato imutável  
- segredos isolados por ambiente  

### Promoção entre ambientes
**Dev → Staging**
- pipeline verde  
- cobertura ≥ 70%  
- sem falhas de segurança  
- PR aprovado  

**Staging → Produção**
- canário estável  
- taxa de erro baixa  
- latência dentro do esperado  
- plano de rollback testado  

---

## 5. Releases e Rollback
Usaremos **canary release**, liberando primeiro para uma parte pequena do tráfego.

### Gatilhos para rollback
- 5xx acima de 2%  
- p95 muito alto  
- erros inesperados nos logs  
- migrações falhando  

O rollback será simples e já terá um passo-a-passo descrito no arquivo RUNBOOK_rollback.md.

---

## 6. Observabilidade e Métricas
### Logs essenciais
- Request log (rota, método, status, tempo)  
- Error log (erro + correlation-id)  

### Métricas observadas
- p95 de latência  
- quantidade de 5xx por minuto  

### Métricas DORA usadas
- Lead time da mudança  
- Change failure rate  
- Frequência de deploy  
- MTTR (quando houver incidente)  

### Rotina PDCA
A cada duas semanas:
- revisar métricas  
- analisar o que deu errado ou melhorou  
- definir 1 ou 2 ações  
- documentar e padronizar o aprendizado  

---

## 7. Maturidade
A maturidade aqui é leve:  
a disciplina vem mais da consistência do processo do que de documentos extensos.

Os principais artefatos são:
- Blueprint  
- Template de PR  
- Política de promoção  
- Pipeline  
- Runbook  
