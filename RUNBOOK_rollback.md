# Runbook de Rollback — Fitness Scheduler API

Este runbook explica de forma simples o que o time deve fazer caso uma versão que foi para produção apresente algum problema.  
O objetivo é ter um passo a passo rápido, claro e fácil de executar, evitando que o sistema fique fora do ar por muito tempo.

---

## Quando usar o rollback?
O rollback deve ser feito quando forem identificados problemas como:

- Aumento de erros **5xx** acima do normal
- Latência p95 muito alta (respostas demorando demais)
- Erros estranhos nos logs
- Falha em migrações ou inicialização
- Comportamento diferente do esperado em produção

---

## Passo a passo do rollback

### 1. Pausar o tráfego para o canário
Se estivermos usando canary release, reduzir o tráfego do canário para 0%.

### 2. Desativar feature flags
Se alguma feature nova estiver ativada, desligar temporariamente.

### 3. Voltar para a versão anterior
No pipeline, selecionar o último artefato estável:
- versão X anterior
- realizar o deploy automático dessa versão

### 4. Acompanhar os gráficos
Monitorar durante alguns minutos:
- taxa de erro
- latência (p95)
- logs de erro

### 5. Registrar o incidente
Adicionar um registro rápido para o time:
- o que aconteceu
- quando aconteceu
- como resolvemos
- ponto para revisar no PDCA

---

## Observações importantes
- O rollback nunca deve ser feito manualmente no servidor.  
- Sempre usar o pipeline para garantir reprodutibilidade.  
- Depois do rollback, a equipe revisa o que causou o problema e cria uma ação de melhoria.
