---
title: "fluxogramas-processos"
category: "CLIENTES"
description: "Cliente: Equipe Santana  "
created: "2025-10-27"
updated: "2025-10-27"
---

# FLUXOGRAMAS DE PROCESSOS - PROJETO SANTANA

**Cliente:** Equipe Santana  
**Projeto:** Sistema Integrado de Atendimento, CRM e Notificações  
**Data:** 22 de Setembro de 2025  
**Versão:** 1.0

---

## 📋 ÍNDICE

1. [Fluxo de Atendimento via WhatsApp](#1-fluxo-de-atendimento-via-whatsapp)
2. [Fluxo de Gestão de Eventos](#2-fluxo-de-gestão-de-eventos)
3. [Fluxo de Notificações Automáticas](#3-fluxo-de-notificações-automáticas)
4. [Fluxo de Gestão de Prestadores](#4-fluxo-de-gestão-de-prestadores)
5. [Fluxo de Integração entre Sistemas](#5-fluxo-de-integração-entre-sistemas)

---

## 1. FLUXO DE ATENDIMENTO VIA WHATSAPP

### 1.1 Fluxo Principal - Primeiro Contato

```
┌─────────────────────────────────────────────────────────────┐
│                    CLIENTE ENVIA MENSAGEM                    │
│                    (WhatsApp Business)                       │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              BOT DETECTA NOVA MENSAGEM                       │
│                   (Chatwoot + n8n)                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                  VERIFICA SE É CLIENTE                       │
│                      EXISTENTE                               │
└────────┬────────────────────────────────────────────────────┘
         │
         ├─── SIM ──────────────────────────────────────┐
         │                                               │
         │                                               ▼
         │                              ┌────────────────────────────┐
         │                              │  BUSCA HISTÓRICO NO CRM    │
         │                              │  Carrega dados do cliente  │
         │                              └────────────┬───────────────┘
         │                                           │
         └─── NÃO ──────────────────────────────────┤
                                                     │
                                                     ▼
                         ┌───────────────────────────────────────────┐
                         │        ENVIA MENSAGEM DE BOAS-VINDAS      │
                         │                                           │
                         │  "Olá! Bem-vindo à Equipe Santana! 👋    │
                         │   Sou o assistente virtual e estou aqui  │
                         │   para ajudar você."                     │
                         └────────────────┬──────────────────────────┘
                                          │
                                          ▼
                         ┌───────────────────────────────────────────┐
                         │         APRESENTA MENU DE OPÇÕES          │
                         │                                           │
                         │  1️⃣ Solicitar Orçamento                   │
                         │  2️⃣ Consultar Evento Agendado            │
                         │  3️⃣ Falar com Atendente                  │
                         │  4️⃣ Ver Portfólio                        │
                         │  5️⃣ Outras Dúvidas                       │
                         └────────────────┬──────────────────────────┘
                                          │
                                          ▼
                         ┌───────────────────────────────────────────┐
                         │       CLIENTE SELECIONA OPÇÃO             │
                         └────────────────┬──────────────────────────┘
                                          │
                ┌─────────────────────────┼─────────────────────────┐
                │                         │                         │
                ▼                         ▼                         ▼
    ┌───────────────────┐   ┌───────────────────┐   ┌───────────────────┐
    │   OPÇÃO 1 ou 5    │   │     OPÇÃO 2       │   │   OPÇÃO 3 ou 4    │
    │   Coleta Dados    │   │  Busca Evento     │   │  Transfere para   │
    │   Básicos         │   │   no CRM          │   │    Atendente      │
    └─────────┬─────────┘   └─────────┬─────────┘   └─────────┬─────────┘
              │                       │                         │
              ▼                       ▼                         ▼
    ┌───────────────────┐   ┌───────────────────┐   ┌───────────────────┐
    │  Cria Lead no CRM │   │ Mostra Informações│   │ Notifica Atendente│
    │  Agenda Callback  │   │   do Evento       │   │  Disponível       │
    └─────────┬─────────┘   └─────────┬─────────┘   └─────────┬─────────┘
              │                       │                         │
              └───────────────────────┴─────────────────────────┘
                                      │
                                      ▼
                         ┌───────────────────────────────────────────┐
                         │      REGISTRA INTERAÇÃO NO CRM            │
                         │      Salva histórico da conversa          │
                         └────────────────┬──────────────────────────┘
                                          │
                                          ▼
                         ┌───────────────────────────────────────────┐
                         │         MENSAGEM DE ENCERRAMENTO          │
                         │                                           │
                         │  "Obrigado pelo contato! Em breve nossa  │
                         │   equipe entrará em contato. 😊"         │
                         └───────────────────────────────────────────┘
```

### 1.2 Fluxo de Qualificação de Lead

```
┌─────────────────────────────────────────────────────────────┐
│              CLIENTE SOLICITA ORÇAMENTO                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                BOT INICIA QUALIFICAÇÃO                       │
│              "Vou fazer algumas perguntas"                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PERGUNTA 1: TIPO DE EVENTO                      │
│  "Qual tipo de evento você está planejando?"                │
│  • Casamento  • Aniversário  • Corporativo  • Outro         │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PERGUNTA 2: DATA DO EVENTO                      │
│  "Qual é a data prevista para o evento?"                    │
│  (Valida se data está disponível)                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PERGUNTA 3: LOCAL                               │
│  "Onde será realizado o evento?"                            │
│  (Cidade/Bairro)                                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PERGUNTA 4: NÚMERO DE CONVIDADOS                │
│  "Quantas pessoas você espera no evento?"                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PERGUNTA 5: SERVIÇOS DESEJADOS                  │
│  "Quais serviços você precisa?"                             │
│  • Foto  • Vídeo  • Som  • Iluminação  • Decoração         │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PERGUNTA 6: ORÇAMENTO                           │
│  "Você tem um orçamento em mente?"                          │
│  (Opcional)                                                 │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              COLETA DADOS DE CONTATO                         │
│  "Para finalizar, preciso de alguns dados:"                 │
│  • Nome completo                                            │
│  • E-mail                                                   │
│  • Telefone (já tem do WhatsApp)                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              CRIA LEAD NO CRM ODOO                           │
│  • Salva todas as informações coletadas                     │
│  • Define status: "Novo Lead"                               │
│  • Atribui para vendedor responsável                        │
│  • Calcula score do lead                                    │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              NOTIFICA EQUIPE COMERCIAL                       │
│  • Envia notificação para vendedor                          │
│  • Inclui resumo do lead                                    │
│  • Define prioridade baseada no score                       │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              MENSAGEM DE CONFIRMAÇÃO                         │
│  "Perfeito! Recebemos sua solicitação. 🎉                   │
│   Nossa equipe entrará em contato em até 24h               │
│   com uma proposta personalizada."                          │
└─────────────────────────────────────────────────────────────┘
```

### 1.3 Fluxo de Transferência para Atendente

```
┌─────────────────────────────────────────────────────────────┐
│         CLIENTE SOLICITA ATENDIMENTO HUMANO                  │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              VERIFICA HORÁRIO DE ATENDIMENTO                 │
└────────┬────────────────────────────────────────────────────┘
         │
         ├─── DENTRO DO HORÁRIO ────────────────────┐
         │                                           │
         │                                           ▼
         │                          ┌────────────────────────────┐
         │                          │  VERIFICA ATENDENTES       │
         │                          │  DISPONÍVEIS               │
         │                          └────────┬───────────────────┘
         │                                   │
         │                    ┌──────────────┴──────────────┐
         │                    │                             │
         │                    ▼                             ▼
         │          ┌──────────────────┐         ┌──────────────────┐
         │          │  TEM DISPONÍVEL  │         │  TODOS OCUPADOS  │
         │          └────────┬─────────┘         └────────┬─────────┘
         │                   │                            │
         │                   ▼                            ▼
         │          ┌──────────────────┐         ┌──────────────────┐
         │          │  TRANSFERE PARA  │         │  COLOCA NA FILA  │
         │          │   ATENDENTE      │         │   DE ESPERA      │
         │          └────────┬─────────┘         └────────┬─────────┘
         │                   │                            │
         │                   └────────────┬───────────────┘
         │                                │
         └─── FORA DO HORÁRIO ────────────┤
                                          │
                                          ▼
                         ┌────────────────────────────────────┐
                         │     MENSAGEM APROPRIADA            │
                         │                                    │
                         │  Dentro: "Conectando você..."      │
                         │  Fila: "Aguarde, você é o Nº X"   │
                         │  Fora: "Retornaremos em horário   │
                         │         comercial"                 │
                         └────────────────┬───────────────────┘
                                          │
                                          ▼
                         ┌────────────────────────────────────┐
                         │    REGISTRA NO CRM                 │
                         │    • Horário da solicitação        │
                         │    • Motivo do contato             │
                         │    • Status do atendimento         │
                         └────────────────────────────────────┘
```

---

## 2. FLUXO DE GESTÃO DE EVENTOS

### 2.1 Fluxo Completo do Evento

```
┌─────────────────────────────────────────────────────────────┐
│                    LEAD QUALIFICADO                          │
│              (Vindo do Bot ou Manual)                        │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              VENDEDOR ANALISA LEAD                           │
│  • Revisa informações coletadas                             │
│  • Verifica viabilidade                                     │
│  • Define estratégia de abordagem                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              CONTATO COM CLIENTE                             │
│  • Ligação ou WhatsApp                                      │
│  • Esclarece dúvidas                                        │
│  • Agenda reunião (se necessário)                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ELABORAÇÃO DE PROPOSTA                          │
│  • Define escopo detalhado                                  │
│  • Calcula custos                                           │
│  • Cria proposta comercial                                  │
│  • Anexa no CRM                                             │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ENVIO DA PROPOSTA                               │
│  • Envia por e-mail                                         │
│  • Compartilha via WhatsApp                                 │
│  • Registra envio no CRM                                    │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ACOMPANHAMENTO                                  │
│  • Follow-up após 2 dias                                    │
│  • Esclarece dúvidas                                        │
│  • Negocia ajustes                                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  CLIENTE APROVA   │   │  CLIENTE RECUSA   │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              │                       ▼
              │              ┌───────────────────┐
              │              │  REGISTRA MOTIVO  │
              │              │  Marca como       │
              │              │  "Perdido"        │
              │              └───────────────────┘
              │
              ▼
┌─────────────────────────────────────────────────────────────┐
│              ASSINATURA DE CONTRATO                          │
│  • Gera contrato no sistema                                 │
│  • Envia para assinatura digital                            │
│  • Aguarda retorno                                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              RECEBIMENTO DE ENTRADA                          │
│  • Registra pagamento no financeiro                         │
│  • Emite recibo/nota fiscal                                 │
│  • Atualiza status: "Confirmado"                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              CRIAÇÃO DO PROJETO/EVENTO                       │
│  • Converte Lead em Cliente                                 │
│  • Cria Projeto no módulo de Eventos                        │
│  • Define todas as informações                              │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PLANEJAMENTO DETALHADO                          │
│  • Cria checklist de tarefas                                │
│  • Define responsáveis                                      │
│  • Estabelece prazos                                        │
│  • Identifica recursos necessários                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ALOCAÇÃO DE PRESTADORES                         │
│  • Identifica prestadores necessários                       │
│  • Verifica disponibilidade                                 │
│  • Faz convites/contratações                                │
│  • Registra no sistema                                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              SISTEMA AGENDA NOTIFICAÇÕES                     │
│  • Notificações para prestadores                            │
│  • Lembretes para cliente                                   │
│  • Alertas para equipe interna                              │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              EXECUÇÃO DO EVENTO                              │
│  • Acompanhamento em tempo real                             │
│  • Checklist de execução                                    │
│  • Registro de ocorrências                                  │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              PÓS-EVENTO                                      │
│  • Marca tarefas como concluídas                            │
│  • Solicita feedback do cliente                             │
│  • Avalia desempenho dos prestadores                        │
│  • Finaliza pagamentos                                      │
│  • Arquiva documentação                                     │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ENCERRAMENTO DO PROJETO                         │
│  • Status: "Concluído"                                      │
│  • Gera relatório final                                     │
│  • Atualiza métricas                                        │
└─────────────────────────────────────────────────────────────┘
```

### 2.2 Fluxo de Gestão de Tarefas

```
┌─────────────────────────────────────────────────────────────┐
│              EVENTO CRIADO NO SISTEMA                        │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              COORDENADOR CRIA TAREFAS                        │
│  • Define lista de atividades                               │
│  • Estabelece dependências                                  │
│  • Define prazos                                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ATRIBUI RESPONSÁVEIS                            │
│  • Designa pessoa para cada tarefa                          │
│  • Notifica responsável                                     │
│  • Define prioridade                                        │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              RESPONSÁVEL RECEBE NOTIFICAÇÃO                  │
│  • Via WhatsApp ou e-mail                                   │
│  • Visualiza detalhes da tarefa                             │
│  • Aceita ou solicita ajustes                               │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              EXECUÇÃO DA TAREFA                              │
│  • Responsável trabalha na atividade                        │
│  • Atualiza progresso no sistema                            │
│  • Adiciona comentários/observações                         │
└────────────────────────┬────────────────────────────────────┘
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  TAREFA CONCLUÍDA │   │  TAREFA BLOQUEADA │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              │                       ▼
              │              ┌───────────────────┐
              │              │  NOTIFICA         │
              │              │  COORDENADOR      │
              │              │  Solicita ajuda   │
              │              └───────────────────┘
              │
              ▼
┌─────────────────────────────────────────────────────────────┐
│              MARCA COMO CONCLUÍDA                            │
│  • Atualiza status                                          │
│  • Notifica coordenador                                     │
│  • Libera tarefas dependentes                               │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              COORDENADOR VALIDA                              │
│  • Revisa trabalho realizado                                │
│  • Aprova ou solicita correções                             │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ATUALIZA PROGRESSO DO EVENTO                    │
│  • Calcula % de conclusão                                   │
│  • Atualiza timeline                                        │
│  • Gera relatório de status                                 │
└─────────────────────────────────────────────────────────────┘
```

---

## 3. FLUXO DE NOTIFICAÇÕES AUTOMÁTICAS

### 3.1 Fluxo de Notificação de Prestadores

```
┌─────────────────────────────────────────────────────────────┐
│              PRESTADOR ALOCADO EM EVENTO                     │
│              (Registro no CRM Odoo)                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              SISTEMA CALCULA DATAS DE NOTIFICAÇÃO            │
│  • 7 dias antes do evento                                   │
│  • 3 dias antes do evento                                   │
│  • 1 dia antes do evento                                    │
│  • 3 horas antes do evento (opcional)                       │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              AGENDA NOTIFICAÇÕES NO n8n                      │
│  • Cria workflows agendados                                 │
│  • Define horários de envio                                 │
│  • Prepara templates de mensagem                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              AGUARDA DATA/HORA PROGRAMADA                    │
│              (n8n monitora continuamente)                    │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              HORÁRIO DE ENVIO ATINGIDO                       │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              BUSCA DADOS DO EVENTO E PRESTADOR               │
│  • Nome do evento                                           │
│  • Data, horário e local                                    │
│  • Função do prestador                                      │
│  • Informações adicionais                                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              MONTA MENSAGEM PERSONALIZADA                    │
│                                                              │
│  "Olá [Nome]! 👋                                            │
│                                                              │
│  Lembrando que você está confirmado para:                   │
│  📅 Evento: [Nome do Evento]                                │
│  📍 Local: [Endereço]                                       │
│  🕐 Data/Hora: [DD/MM às HH:MM]                            │
│  👤 Função: [Sua Função]                                    │
│                                                              │
│  Por favor, confirme sua presença respondendo:              │
│  ✅ SIM - Estarei presente                                  │
│  ❌ NÃO - Não poderei comparecer"                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ENVIA MENSAGEM VIA WHATSAPP                     │
│              (WhatsApp Business API)                         │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              REGISTRA ENVIO NO CRM                           │
│  • Data/hora do envio                                       │
│  • Status: "Enviado"                                        │
│  • Aguarda resposta                                         │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              AGUARDA RESPOSTA DO PRESTADOR                   │
│              (Timeout: 24 horas)                             │
└────────────────────────┬────────────────────────────────────┘
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  CONFIRMOU (✅)   │   │  RECUSOU (❌)     │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              ▼                       ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  Atualiza Status  │   │  Notifica         │
    │  "Confirmado"     │   │  Coordenador      │
    │  Envia mensagem   │   │  Busca substituto │
    │  de agradecimento │   │                   │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              └───────────┬───────────┘
                          │
                          ▼
                ┌───────────────────┐
                │  NÃO RESPONDEU    │
                └─────────┬─────────┘
                          │
                          ▼
                ┌───────────────────┐
                │  ENVIA LEMBRETE   │
                │  "Ainda aguardamos│
                │   sua confirmação"│
                └─────────┬─────────┘
                          │
                          ▼
                ┌───────────────────┐
                │  Aguarda mais 12h │
                └─────────┬─────────┘
                          │
                ┌─────────┴─────────┐
                │                   │
                ▼                   ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  RESPONDEU        │   │  AINDA NÃO        │
    │  (Processa)       │   │  RESPONDEU        │
    └───────────────────┘   └─────────┬─────────┘
                                      │
                                      ▼
                            ┌───────────────────┐
                            │  NOTIFICA         │
                            │  COORDENADOR      │
                            │  Contato manual   │
                            │  necessário       │
                            └───────────────────┘
```

### 3.2 Fluxo de Notificação de Clientes

```
┌─────────────────────────────────────────────────────────────┐
│              EVENTO CONFIRMADO NO SISTEMA                    │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ENVIA CONFIRMAÇÃO IMEDIATA                      │
│  "Seu evento foi confirmado! 🎉                             │
│   Detalhes: [resumo do evento]"                             │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              AGENDA LEMBRETES                                │
│  • 7 dias antes: Lembrete geral                             │
│  • 3 dias antes: Confirmação de detalhes                    │
│  • 1 dia antes: Lembrete final                              │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              NO DIA DO EVENTO                                │
│  • Mensagem de bom dia                                      │
│  • Confirmação de que tudo está pronto                      │
│  • Contato da equipe responsável                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              APÓS O EVENTO (1-2 dias)                        │
│  • Agradecimento                                            │
│  • Solicitação de feedback                                  │
│  • Link para avaliação                                      │
└─────────────────────────────────────────────────────────────┘
```

---

## 4. FLUXO DE GESTÃO DE PRESTADORES

### 4.1 Fluxo de Cadastro de Prestador

```
┌─────────────────────────────────────────────────────────────┐
│              NOVO PRESTADOR IDENTIFICADO                     │
│              (Indicação ou Busca Ativa)                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              COLETA DE INFORMAÇÕES BÁSICAS                   │
│  • Nome completo                                            │
│  • CPF/CNPJ                                                 │
│  • Telefone/WhatsApp                                        │
│  • E-mail                                                   │
│  • Endereço                                                 │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              INFORMAÇÕES PROFISSIONAIS                       │
│  • Especialidade/Função                                     │
│  • Experiência (anos)                                       │
│  • Portfólio (links/fotos)                                  │
│  • Equipamentos próprios                                    │
│  • Certificações                                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              INFORMAÇÕES COMERCIAIS                          │
│  • Valor/hora ou por evento                                 │
│  • Forma de pagamento preferida                             │
│  • Disponibilidade (dias/horários)                          │
│  • Raio de atuação (km)                                     │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              DOCUMENTAÇÃO                                    │
│  • RG/CNH (cópia)                                           │
│  • CPF (cópia)                                              │
│  • Comprovante de residência                                │
│  • Certificados (se aplicável)                              │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              CADASTRO NO SISTEMA ODOO                        │
│  • Cria registro no módulo de Colaboradores                 │
│  • Anexa documentos                                         │
│  • Define tags/categorias                                   │
│  • Status: "Ativo"                                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              TESTE/AVALIAÇÃO INICIAL                         │
│  • Convite para primeiro evento                             │
│  • Acompanhamento próximo                                   │
│  • Avaliação de desempenho                                  │
└────────────────────────┬────────────────────────────────────┘
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  APROVADO         │   │  NÃO APROVADO     │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              ▼                       ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  Adiciona ao pool │   │  Marca como       │
    │  de prestadores   │   │  "Inativo"        │
    │  regulares        │   │  Registra motivo  │
    └───────────────────┘   └───────────────────┘
```

### 4.2 Fluxo de Alocação de Prestador

```
┌─────────────────────────────────────────────────────────────┐
│              EVENTO PRECISA DE PRESTADORES                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              IDENTIFICA NECESSIDADES                         │
│  • Quais funções são necessárias                            │
│  • Quantos profissionais por função                         │
│  • Requisitos específicos                                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              BUSCA PRESTADORES DISPONÍVEIS                   │
│  • Filtra por especialidade                                 │
│  • Verifica disponibilidade na data                         │
│  • Considera localização                                    │
│  • Ordena por avaliação/experiência                         │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              SELECIONA PRESTADORES                           │
│  • Escolhe os melhores candidatos                           │
│  • Considera histórico de trabalhos                         │
│  • Verifica compatibilidade                                 │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ENVIA CONVITE                                   │
│  • Via WhatsApp                                             │
│  • Detalhes do evento                                       │
│  • Valor a ser pago                                         │
│  • Prazo para resposta                                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              AGUARDA CONFIRMAÇÃO                             │
│              (Prazo: 24-48 horas)                            │
└────────────────────────┬────────────────────────────────────┘
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  ACEITA           │   │  RECUSA           │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              ▼                       ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  Confirma alocação│   │  Busca próximo    │
    │  Envia detalhes   │   │  candidato        │
    │  completos        │   │  Repete processo  │
    └─────────┬─────────┘   └───────────────────┘
              │
              ▼
┌─────────────────────────────────────────────────────────────┐
│              REGISTRA NO EVENTO                              │
│  • Adiciona prestador ao evento                             │
│  • Define função e responsabilidades                        │
│  • Agenda notificações                                      │
└─────────────────────────────────────────────────────────────┘
```

---

## 5. FLUXO DE INTEGRAÇÃO ENTRE SISTEMAS

### 5.1 Fluxo de Sincronização Chatwoot ↔ Odoo

```
┌─────────────────────────────────────────────────────────────┐
│              NOVA CONVERSA NO CHATWOOT                       │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              n8n DETECTA WEBHOOK                             │
│              (Trigger: Nova Mensagem)                        │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              EXTRAI INFORMAÇÕES                              │
│  • Número do cliente                                        │
│  • Nome (se disponível)                                     │
│  • Conteúdo da mensagem                                     │
│  • Timestamp                                                │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              BUSCA CLIENTE NO ODOO                           │
│              (Por telefone ou e-mail)                        │
└────────────────────────┬────────────────────────────────────┘
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  CLIENTE EXISTE   │   │  CLIENTE NOVO     │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              ▼                       ▼
    ┌───────────────────┐   ┌───────────────────┐
    │  Carrega dados    │   │  Cria novo        │
    │  existentes       │   │  registro         │
    └─────────┬─────────┘   └─────────┬─────────┘
              │                       │
              └───────────┬───────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              REGISTRA INTERAÇÃO NO CRM                       │
│  • Cria nota/atividade                                      │
│  • Anexa conteúdo da conversa                               │
│  • Atualiza última interação                                │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              SE LEAD QUALIFICADO                             │
│  • Cria oportunidade no CRM                                 │
│  • Notifica vendedor responsável                            │
│  • Agenda follow-up                                         │
└─────────────────────────────────────────────────────────────┘
```

### 5.2 Fluxo de Sincronização Odoo → WhatsApp

```
┌─────────────────────────────────────────────────────────────┐
│              EVENTO CRIADO/ATUALIZADO NO ODOO                │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ODOO DISPARA WEBHOOK                            │
│              (Trigger: Mudança de Status)                    │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              n8n RECEBE NOTIFICAÇÃO                          │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              IDENTIFICA TIPO DE AÇÃO                         │
└────────────────────────┬────────────────────────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
┌───────────────┐ ┌───────────────┐ ┌───────────────┐
│ NOVO EVENTO   │ │ ATUALIZAÇÃO   │ │ CANCELAMENTO  │
└───────┬───────┘ └───────┬───────┘ └───────┬───────┘
        │                 │                 │
        └─────────────────┼─────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              PREPARA MENSAGEM APROPRIADA                     │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              ENVIA VIA WHATSAPP API                          │
│  • Para cliente                                             │
│  • Para prestadores (se aplicável)                          │
│  • Para equipe interna (se necessário)                      │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              REGISTRA ENVIO NO ODOO                          │
│  • Atualiza histórico de comunicação                        │
│  • Marca como notificado                                    │
└─────────────────────────────────────────────────────────────┘
```

---

## 📊 LEGENDA DOS FLUXOGRAMAS

### Símbolos Utilizados

```
┌─────────────────┐
│   PROCESSO      │  = Ação ou processo
└─────────────────┘

        │
        ▼            = Fluxo/Direção

┌─────────────────┐
│   DECISÃO?      │  = Ponto de decisão
└────────┬────────┘
         │
    ┌────┴────┐
    │         │
   SIM       NÃO

[Texto]              = Observação ou detalhe adicional
```

### Status e Estados

- **Novo**: Registro recém-criado
- **Em Andamento**: Processo em execução
- **Aguardando**: Esperando ação externa
- **Concluído**: Processo finalizado
- **Cancelado**: Processo interrompido
- **Bloqueado**: Impedimento identificado

---

## 📝 NOTAS DE IMPLEMENTAÇÃO

### Prioridades de Desenvolvimento

1. **Fase 1 - Crítico**
   - Fluxo de atendimento básico
   - Criação de leads no CRM
   - Notificações simples

2. **Fase 2 - Importante**
   - Gestão completa de eventos
   - Alocação de prestadores
   - Notificações avançadas

3. **Fase 3 - Desejável**
   - Automações complexas
   - Relatórios avançados
   - Integrações adicionais

### Pontos de Atenção

⚠️ **Tratamento de Erros**
- Todos os fluxos devem ter tratamento de exceções
- Logs detalhados para debugging
- Notificações de falhas para administradores

⚠️ **Performance**
- Otimizar consultas ao banco de dados
- Implementar cache quando apropriado
- Monitorar tempo de resposta

⚠️ **Segurança**
- Validar todas as entradas
- Criptografar dados sensíveis
- Implementar rate limiting

---

## ✅ CHECKLIST DE VALIDAÇÃO

Antes de implementar cada fluxo, verificar:

- [ ] Todos os cenários possíveis foram mapeados?
- [ ] Tratamento de erros está definido?
- [ ] Notificações necessárias estão incluídas?
- [ ] Integrações entre sistemas estão claras?
- [ ] Performance foi considerada?
- [ ] Segurança foi avaliada?
- [ ] Logs e auditoria estão previstos?
- [ ] Testes foram planejados?

---

**Documento preparado por:** Johnny / Tarcísio (Jidu Marketing Digital)  
**Versão:** 1.0  
**Data:** 22/09/2025  
**Próxima Revisão:** Após levantamento de requisitos com cliente