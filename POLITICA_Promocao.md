# Política de Promoção — Fitness Scheduler API

Esta política define quando uma versão pode ser promovida entre os ambientes: **dev**, **staging** e **produção**.  
O objetivo é garantir que as entregas sejam feitas com segurança, sem burocracia, mas com responsabilidade.

---

## Promoção de Dev → Staging
A versão só pode ir para o ambiente de **staging** quando:

- Pipeline passou sem erros
- Cobertura de testes ficou acima de 70%
- Lint sem erros
- SAST sem alertas críticos
- PR revisado e aprovado
- Logs e comportamento funcionaram como esperado no ambiente de dev

A ideia é que staging só receba algo “quase pronto para produção”.

---

## Promoção de Staging → Produção
Para ir para produção, precisamos de um pouco mais de cuidado. A versão só é promovida se:

- O canário funcionou sem problemas
- Taxa de erro 5xx baixa (próximo de 0%)
- Latência p95 dentro do esperado
- Não apareceu nada anormal nos logs
- O rollback está funcionando (testado)
- O PO confirmou se houver mudança que impacta o usuário

---

## Evidências necessárias
Antes de promover, o time registra evidências simples para consulta rápida:

- Print ou link da pipeline verde
- Métricas principais (latência e erros)
- O que mudou nessa release
- Confirmação que o rollback foi testado

Tudo isso pode ser colocado na própria descrição do PR ou no board da equipe.

---

## Princípios gerais
- Sem pressa para subir versão com risco
- Produção só recebe artefatos que já passaram por todas as etapas
- Se algo parecer estranho, volta para dev
- Qualidade antes de velocidade
- Segurança antes de novidade

---

## Quando NÃO promover
A versão nunca deve ser promovida quando:

- Não passou na pipeline
- Há erro crítico ou alerta de segurança
- Métricas ruins no canário
- Falha em testes de migração
- PR sem revisão

Esses pontos evitam instabilidades em produção.

---

## Objetivo final
O foco da política é manter um fluxo previsível e evitar apagar incêndios.  
A maturidade é leve, mas suficiente para garantir segurança e organização no processo de entrega.
