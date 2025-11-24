# Fitness Scheduler — Blueprint do Downstream  
Projeto da disciplina *Análise, Projeto e Desenvolvimento Ágil*  
Professor: **Edson Vaz Lopes**

---

## 👥 Alunos
- **Eder Duarte Zerek**  
- **José Lucas Andrade Fonseca**  
- **Leonardo Henrique Fernandes Nascimento**  
- **Sidney Cardoso de Oliveira Junior**

---

## 📘 Sobre o Projeto
Este repositório contém todos os artefatos do *Blueprint do Downstream* para a **Fitness Scheduler API**, uma API simples usada apenas como exemplo acadêmico.  
O foco não é o código da aplicação, mas sim demonstrar como um time aplica práticas de downstream, garantindo qualidade, organização e segurança nas entregas.

Entre os conceitos aplicados:
- organização com Git e Pull Requests  
- controle de qualidade  
- pirâmide de testes  
- pipeline CI/CD  
- ambientes (dev → staging → produção)  
- estratégia de release e rollback  
- observabilidade e métricas DORA  
- PDCA e melhoria contínua  
- maturidade leve  

---

## 📂 Estrutura do Repositório

```
📁 fitness-scheduler-downstream
├── Blueprint.md
├── POLITICA_Promocao.md
├── RUNBOOK_rollback.md
├── README.md
└── .github/
     ├── PULL_REQUEST_TEMPLATE.md
     └── workflows/
          └── ci.yml
```

---

## 🧩 Descrição dos Arquivos

### **Blueprint.md**
Documento principal do trabalho.  
Resume como o time organizaria todo o downstream da API.

### **PULL_REQUEST_TEMPLATE.md**
Modelo de Pull Request usado para padronizar revisões.

### **ci.yml**
Pipeline mínimo com etapas essenciais (lint, testes, cobertura, SAST e build).

### **RUNBOOK_rollback.md**
Guia rápido de rollback caso a versão apresente falhas em produção.

### **POLITICA_Promocao.md**
Regras para promoção entre dev → staging → produção.

---

## 🚀 Objetivo Acadêmico
Demonstrar entendimento prático das práticas de downstream da Unidade 3, incluindo:
- qualidade  
- automação  
- previsibilidade  
- segurança  
- governança leve  

---

## 📄 Licença
Projeto acadêmico — livre para consulta e estudo.
