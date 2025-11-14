
---

# 📘 **README — Documentação do Modelo Dimensional (Versão Ajustada)**

```markdown
📊 Documentação do Modelo Dimensional

Este repositório contém a documentação completa das tabelas utilizadas no modelo analítico, incluindo **tabelas fato**, **tabelas dimensão** e **tabelas agregadas**.  
O objetivo é centralizar, padronizar e facilitar o entendimento da estrutura de dados utilizada para análises, dashboards, integrações e processos de Business Intelligence.

Toda a documentação foi organizada em arquivos individuais, um para cada tabela, garantindo fácil navegação e manutenção.

---

## 🎯 Objetivo da Documentação

- Padronizar o entendimento estrutural das tabelas.  
- Facilitar onboarding de novos analistas, engenheiros e cientistas de dados.  
- Auxiliar na construção de queries SQL consistentes.  
- Servir como base para criação de pipelines, dashboards e análises avançadas.  
- Registrar relacionamento entre entidades e chaves primárias/estrangeiras.  

---

## 🧱 Estrutura Geral

A documentação descreve para cada tabela:

- **Descrição Geral**  
  Contexto, finalidade e uso da tabela no ecossistema de dados.

- **Tabela Técnica**  
  Lista completa das colunas com tipo de dado, descrição técnica e chaves.

- **Relacionamentos**  
  Principais integrações com outras tabelas do modelo dimensional.

- **Exemplos de uso** (quando aplicável)  
  SQLs úteis para entendimento e navegação.

---

## 📂 Tabelas Documentadas

As tabelas estão organizadas por categoria:

### 🔷 Dimensões
- dvendedores  
- dClientes  
- dAssociados  
- dCalendario  
- dCarteirizacao  
- dCupons  
- dDispositivos  
- dFeriados  
- dGrupo_Cliente  
- dMetodo_pagamento  
- dOfertas  
- dPeriodos  
- dProdutos  
- dStatus_pedido  
- dTipo_envio  
- dTipo_pedido  

### 🟦 Fatos
- fVendas  
- fLogins  
- fDatalayer_session_summary  
- fDatalayer_product_pageviews  
- fCarrinhos_abandonados  

### 🟩 Agregações
- agg_last_login  
- agg_last_purchase  

---

## 📐 Modelo Dimensional

O conjunto das tabelas descritas compõe um **Data Warehouse orientado a análise**, permitindo:

- Análises do desempenho comercial  
- Segmentação e comportamento de clientes  
- Monitoramento de engajamento digital  
- Acompanhamento de vendas e produtos  
- Integração com ferramentas de BI e Data Science  

---

## 📎 Fonte

A documentação foi elaborada a partir do arquivo original:

**Documentação_tabela_versao_1.pdf**  
*(link ou referência interna ao repositório)*

---

## 🧩 Como navegar

Cada tabela possui seu próprio arquivo README, localizado em:

```

/tabelas/
dvendedores.md
dClientes.md
fVendas.md
...

```

---

## 🤝 Contribuindo

Sugestões, correções e melhorias são bem-vindas!  
Mantenha o padrão de documentação para consistência em todo o repositório.

---

## 📄 Licença

Este repositório segue a política interna da organização.  
Utilize e compartilhe conforme permitido pelas diretrizes do projeto.
```

---


