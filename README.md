---
title: "README"
category: "CLIENTES"
description: "Cliente: Equipe Santana  "
created: "2025-10-27"
updated: "2025-10-27"
---

# 📁 PROJETO GRUPO SANTANA CAMPINAS - DOCUMENTAÇÃO COMPLETA

**Cliente:** Grupo Santana Campinas
**Projeto:** Sistema Integrado de Atendimento, CRM e Notificações
**Data de Início:** 22 de Setembro de 2025
**Status:** 🟡 Em Planejamento
**Desenvolvedor:** Johnny
**Coordenação:** Tarcísio Santos (Jidu Marketing Digital)

---

## 🏢 SOBRE O CLIENTE

**Grupo Santana Campinas** é uma empresa sólida e conceituada que atua há mais de 15 anos nas áreas de:
- **Sermedica:** Ambulâncias e Atendimento Pré-Hospitalar (USB/USA)
- **Serfire:** Bombeiros Profissionais Civis e Guarda-Vidas
- **Serfire Engenharia:** Alvarás, AVCB/CLCB e Sistemas Contra Incêndio
- **Horto Fire:** Escola de Treinamento e Capacitação Profissional

**Slogan:** "Inovação e Versatilidade Movidas Por Responsabilidade Para Sua Empresa"

**Contato:**
- 📞 (19) 3367-7015 | (19) 97409-7142 | (19) 99915-6562
- 📧 comercial@gruposantanacampinas.com.br
- 📍 Rua Geraldo Paulino, Nº09, São Bernardo, Campinas/SP - CEP 13.030-630
- 🕐 Atendimento 24 HORAS

---

## 📋 VISÃO GERAL DO PROJETO

Sistema completo para automação de atendimento via WhatsApp, gestão de relacionamento com clientes (CRM) e notificações automáticas para coordenação de eventos, profissionais (médicos, enfermeiros, bombeiros, guarda-vidas) e prestadores de serviço do Grupo Santana.

### 🎯 Objetivos Principais

1. **Atendimento Automatizado** - Bot de WhatsApp para primeiro contato e direcionamento
2. **Gestão Centralizada** - CRM Odoo para clientes, eventos e prestadores
3. **Comunicação Proativa** - Sistema de notificações automáticas via WhatsApp

### 💰 Investimento

**Implementação (Único):** R$ 4.400,00
- Coordenação (Tarcísio): R$ 1.400,00
- Desenvolvimento (Johnny): R$ 3.000,00

**Mensalidade:** R$ 250,00
- Servidor VPS: R$ 80,00
- Manutenção Odoo: R$ 170,00

### ⏱️ Prazo

**38 dias úteis** (~8 semanas)

---

## 📂 ESTRUTURA DA DOCUMENTAÇÃO

### 📊 [00-Informacoes-Empresa](./00-Informacoes-Empresa/)
Informações detalhadas sobre o Grupo Santana

- **[dados-grupo-santana.md](./00-Informacoes-Empresa/dados-grupo-santana.md)**
  - Dados completos da empresa coletados do site oficial
  - Serviços oferecidos por cada empresa do grupo
  - Profissionais e especialidades
  - Segmentos de atuação
  - Diferenciais competitivos
  - Necessidades identificadas para o projeto

### � [01-Contrato](./01-Contrato/)
Documentação legal e comercial do projeto

- **[contrato-prestacao-servicos-santana.md](./01-Contrato/contrato-prestacao-servicos-santana.md)**
  - Contrato completo de prestação de serviços
  - Escopo detalhado
  - Valores e formas de pagamento
  - Prazos e garantias
  - Obrigações de ambas as partes

### 📊 [02-Briefing](./02-Briefing/)
Planejamento estratégico e visão do projeto

- **[briefing-projeto-santana.md](./02-Briefing/briefing-projeto-santana.md)**
  - Sumário executivo
  - Contexto do negócio
  - Solução proposta
  - Arquitetura do sistema
  - Cronograma detalhado
  - Métricas de sucesso
  - Riscos e mitigações

### 📝 [03-Levantamento](./03-Levantamento/)
Coleta de requisitos e informações do cliente

- **[questionario-levantamento-requisitos.md](./03-Levantamento/questionario-levantamento-requisitos.md)**
  - 71 perguntas organizadas em 13 seções
  - Informações gerais da empresa
  - Estrutura organizacional
  - Processos atuais
  - Necessidades específicas
  - Expectativas e prioridades

### 🔄 [04-Fluxos](./04-Fluxos/)
Fluxogramas e processos do sistema

- **[fluxogramas-processos.md](./04-Fluxos/fluxogramas-processos.md)**
  - Fluxo de atendimento via WhatsApp
  - Fluxo de gestão de eventos
  - Fluxo de notificações automáticas
  - Fluxo de gestão de prestadores
  - Fluxo de integração entre sistemas

### ✅ [05-Checklist](./05-Checklist/)
Acompanhamento da implementação

- **[checklist-implementacao.md](./05-Checklist/checklist-implementacao.md)**
  - Fase 0: Pré-Projeto
  - Fase 1: Planejamento e Levantamento (3 dias)
  - Fase 2: Configuração de Infraestrutura (5 dias)
  - Fase 3: Implementação do Bot WhatsApp (7 dias)
  - Fase 4: Configuração do CRM Odoo (10 dias)
  - Fase 5: Sistema de Notificações (5 dias)
  - Fase 6: Testes e Homologação (5 dias)
  - Fase 7: Treinamento e Entrega (3 dias)
  - Fase 8: Pós-Go-Live

### 🔧 [06-Documentacao-Tecnica](./06-Documentacao-Tecnica/)
Especificações técnicas e arquitetura

- **[documentacao-tecnica.md](./06-Documentacao-Tecnica/documentacao-tecnica.md)**
  - Arquitetura do sistema
  - Stack tecnológico
  - Infraestrutura e servidores
  - Configurações detalhadas
  - Integrações e APIs
  - Segurança e backups
  - Monitoramento e manutenção
  - Troubleshooting

---

## 🛠️ STACK TECNOLÓGICO

### Infraestrutura
- **Servidor:** VPS Ubuntu 22.04 LTS (4GB RAM, 2 vCPUs, 80GB SSD)
- **Proxy:** Nginx com SSL/TLS (Let's Encrypt)
- **Banco de Dados:** PostgreSQL 14+
- **Cache:** Redis 6.2+

### Aplicações
- **CRM:** Odoo 17 (Python)
- **Atendimento:** Chatwoot 3.0+ (Node.js)
- **Automação:** n8n 1.0+ (Node.js)
- **WhatsApp:** WhatsApp Business API

### Containerização
- **Docker:** 24+
- **Docker Compose:** Para orquestração

---

## 📅 CRONOGRAMA RESUMIDO

| Fase | Duração | Período | Status |
|------|---------|---------|--------|
| **Fase 0:** Pré-Projeto | - | Antes do início | ⏳ Pendente |
| **Fase 1:** Planejamento | 3 dias | Semana 1 | ⏳ Pendente |
| **Fase 2:** Infraestrutura | 5 dias | Semana 1-2 | ⏳ Pendente |
| **Fase 3:** Bot WhatsApp | 7 dias | Semana 2-3 | ⏳ Pendente |
| **Fase 4:** CRM Odoo | 10 dias | Semana 3-5 | ⏳ Pendente |
| **Fase 5:** Notificações | 5 dias | Semana 5-6 | ⏳ Pendente |
| **Fase 6:** Testes | 5 dias | Semana 6-7 | ⏳ Pendente |
| **Fase 7:** Treinamento | 3 dias | Semana 7-8 | ⏳ Pendente |
| **Fase 8:** Pós-Go-Live | Contínuo | Após entrega | ⏳ Pendente |

**Total:** 38 dias úteis (~8 semanas)

---

## 🎯 PRINCIPAIS FUNCIONALIDADES

### 1️⃣ Bot de WhatsApp
- ✅ Atendimento automático 24/7
- ✅ Qualificação de leads
- ✅ Menu interativo
- ✅ Direcionamento inteligente
- ✅ Histórico de conversas

### 2️⃣ CRM Odoo
- ✅ Gestão de clientes
- ✅ Pipeline de vendas
- ✅ Gestão de eventos/projetos
- ✅ Cadastro de prestadores
- ✅ Relatórios e dashboards
- ✅ Controle de tarefas

### 3️⃣ Sistema de Notificações
- ✅ Notificações automáticas via WhatsApp
- ✅ Lembretes programados (7, 3, 1 dia antes)
- ✅ Confirmação de presença
- ✅ Alertas de última hora
- ✅ Feedback pós-evento

---

## 📊 MÉTRICAS DE SUCESSO

### KPIs de Atendimento
- Tempo médio de primeira resposta
- Taxa de resolução no primeiro contato
- Satisfação do cliente (NPS)
- Volume de atendimentos

### KPIs de Gestão
- Número de eventos gerenciados
- Taxa de conclusão de tarefas
- Tempo médio de ciclo de evento
- Utilização de prestadores

### KPIs de Comunicação
- Taxa de entrega de notificações
- Taxa de confirmação de colaboradores
- Tempo médio de resposta
- Redução de no-shows

---

## 👥 EQUIPE DO PROJETO

### Desenvolvimento
**Johnny** - Desenvolvedor Full Stack
- Responsável pela implementação técnica
- Configuração de servidores
- Desenvolvimento de integrações
- Testes e deploy

### Coordenação
**Tarcísio Santos** - Jidu Marketing Digital
- Coordenação geral do projeto
- Planejamento estratégico
- Relacionamento com cliente
- Treinamento e suporte

### Cliente
**Equipe Santana**
- Fornecimento de requisitos
- Validação de entregas
- Testes de homologação
- Feedback contínuo

---

## 📞 CONTATOS

### Jidu Marketing Digital
- **Telefone:** +55 (19) 98865-6571
- **E-mail:** santos@jidu.com.br
- **Site:** www.jidu.com.br
- **Instagram:** @jidudigital

### Suporte Técnico
- **Desenvolvedor:** Johnny
- **Horário:** Comercial (8h-18h)
- **Canais:** WhatsApp, E-mail, Telefone

---

## 📝 PRÓXIMOS PASSOS

### Para Iniciar o Projeto

1. ✅ **Revisar Documentação**
   - Ler contrato completo
   - Entender briefing do projeto
   - Revisar fluxogramas

2. ⏳ **Assinatura do Contrato**
   - Assinar contrato de prestação de serviços
   - Confirmar valores e prazos

3. ⏳ **Pagamento de Entrada**
   - Efetuar pagamento de 50% (R$ 1.500,00)
   - Enviar comprovante

4. ⏳ **Levantamento de Requisitos**
   - Agendar reunião de kickoff
   - Preencher questionário completo
   - Fornecer dados para migração

5. ⏳ **Início da Implementação**
   - Configuração de infraestrutura
   - Desenvolvimento dos sistemas
   - Testes e validações

---

## 🔒 SEGURANÇA E PRIVACIDADE

### Medidas Implementadas
- ✅ Criptografia SSL/TLS em todas as comunicações
- ✅ Autenticação de dois fatores
- ✅ Backup diário automático
- ✅ Firewall configurado
- ✅ Atualizações de segurança regulares

### Conformidade LGPD
- ✅ Política de privacidade
- ✅ Termo de consentimento
- ✅ Controle de acesso por perfil
- ✅ Logs de auditoria
- ✅ Direito ao esquecimento

---

## 📚 RECURSOS ADICIONAIS

### Documentação de Referência
- [Odoo Documentation](https://www.odoo.com/documentation)
- [Chatwoot Documentation](https://www.chatwoot.com/docs)
- [n8n Documentation](https://docs.n8n.io)
- [WhatsApp Business API](https://developers.facebook.com/docs/whatsapp)

### Tutoriais e Guias
- Guia de uso do CRM Odoo
- Manual do atendente Chatwoot
- Configuração de workflows n8n
- Boas práticas de atendimento

---

## 🔄 CONTROLE DE VERSÕES

| Versão | Data | Autor | Alterações |
|--------|------|-------|------------|
| 1.0 | 22/09/2025 | Johnny | Documentação inicial completa |

---

## ✅ STATUS DO PROJETO

**Última Atualização:** 22/09/2025

### Documentação
- [x] Contrato elaborado
- [x] Briefing completo
- [x] Questionário de levantamento
- [x] Fluxogramas desenhados
- [x] Checklist de implementação
- [x] Documentação técnica

### Implementação
- [ ] Contrato assinado
- [ ] Pagamento de entrada
- [ ] Levantamento de requisitos
- [ ] Infraestrutura configurada
- [ ] Bot WhatsApp implementado
- [ ] CRM Odoo configurado
- [ ] Sistema de notificações
- [ ] Testes realizados
- [ ] Treinamento concluído
- [ ] Go-live realizado

---

## 📧 FEEDBACK E SUPORTE

Para dúvidas, sugestões ou suporte técnico:

**E-mail:** santos@jidu.com.br  
**WhatsApp:** +55 (19) 98865-6571  
**Horário:** Segunda a Sexta, 8h às 18h

---

**Desenvolvido por:** Johnny & Tarcísio Santos (Jidu Marketing Digital)  
**Proposta Original:** [jidu-Equipe-Santana_.pdf](../../CLIENTES/SANTANA/jidu-Equipe-Santana_.pdf)  
**Versão:** 1.0  
**Data:** 22 de Setembro de 2025