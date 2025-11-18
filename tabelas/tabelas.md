# Documentação do Modelo de Dados


## 📊 Tabela: `dvendedores`

**Descrição Geral**  
Armazena informações cadastrais, hierárquicas, geográficas e comerciais dos vendedores. Cada registro representa um vendedor único.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador único do vendedor                                           | Chave Primária         |
| account_create_date          | DATE             | Data de criação da conta                                                  | —                      |
| client_id                    | INTEGER          | Código do cliente associado                                               | Chave Estrangeira      |
| client_status                | BOOLEAN          | Status ativo/inativo do cliente                                           | —                      |
| account_origin               | VARCHAR(50)      | Canal de origem do cadastro                                               | —                      |
| client_create_date           | DATE             | Data de criação do cliente vinculado                                      | —                      |
| name                         | VARCHAR(150)     | Nome completo ou razão social                                             | —                      |
| contact                      | VARCHAR(150)     | Contato principal do vendedor                                             | —                      |
| account_user                 | VARCHAR(150)     | Login ou e-mail de acesso                                                 | —                      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do vendedor                                                   | —                      |
| gender                       | VARCHAR(20)      | Gênero informado                                                          | —                      |
| person_type                  | VARCHAR(10)      | Tipo de pessoa (PF/PJ)                                                    | —                      |
| age                          | INTEGER          | Idade do vendedor                                                         | —                      |
| country                      | VARCHAR(50)      | País de origem                                                            | —                      |
| UF                           | VARCHAR(5)       | Unidade Federativa                                                        | —                      |
| state                        | VARCHAR(50)      | Estado                                                                    | —                      |
| region                       | VARCHAR(30)      | Região geográfica derivada                                                | —                      |
| city                         | VARCHAR(100)     | Cidade                                                                    | —                      |
| zip_code                     | VARCHAR(15)      | Código postal (CEP)                                                       | —                      |
| phone_number                 | VARCHAR(20)      | Telefone de contato                                                       | —                      |
| CNAE                         | VARCHAR(15)      | Código de atividade econômica                                             | —                      |
| wpp_opt_in                   | BOOLEAN          | Indica aceitação de comunicação via WhatsApp                              | —                      |
| salesperson_account_id       | INTEGER          | ID do vendedor responsável                                                | Chave Estrangeira      |
| salesperson_document         | VARCHAR(20)      | CPF do vendedor responsável                                               | —                      |
| site_id                      | INTEGER          | Canal ou site de origem                                                   | —                      |
| client_last_updated          | DATE             | Data da última atualização cadastral                                      | —                      |
| profile_picture              | VARCHAR(255)     | URL da imagem de perfil                                                   | —                      |
| line                         | VARCHAR(50)      | Linha ou categoria comercial                                              | —                      |
| total_credit_limit           | DECIMAL(18,2)    | Limite máximo de crédito                                                  | —                      |
| credit_balance               | DECIMAL(18,2)    | Saldo de crédito disponível                                               | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | —                      |
| salesperson_code             | VARCHAR(20)      | Código interno do vendedor                                                | —                      |
| salesperson_document_code    | VARCHAR(20)      | CPF interno cadastrado                                                    | —                      |
| client_segment               | VARCHAR(10)      | Código de segmentação comercial                                           | —                      |
| segment_description          | VARCHAR(100)     | Descrição do segmento                                                     | —                      |
| division                     | VARCHAR(30)      | Divisão comercial                                                         | —                      |

---

## 🧾 Tabela: `ólendas` (Fato de Vendas)

**Descrição Geral**  
Tabela fato central que consolida todas as transações comerciais. Cada registro representa uma linha de pedido.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| amount_charged               | DECIMAL(18,2)    | Valor total cobrado na venda                                              | —                      |
| avg_credit_card_interest     | DECIMAL(10,4)    | Média dos juros sobre cartão de crédito                                   | —                      |
| avg_total_tax                | DECIMAL(10,4)    | Média de impostos aplicados                                               | —                      |
| cart_order_id                | INTEGER          | Identificador do carrinho de compra                                       | —                      |
| client_account_id            | INTEGER          | Referência ao cliente comprador                                           | Chave Estrangeira      |
| coupon_id                    | VARCHAR(50)      | Código do cupom promocional                                               | —                      |
| datekey                      | INTEGER          | Chave temporal da data da transação                                       | Chave Estrangeira      |
| datekey_faturamento          | INTEGER          | Data de faturamento da venda                                              | —                      |
| device_id                    | VARCHAR(50)      | Identificador do dispositivo de compra                                    | —                      |
| discount_value               | DECIMAL(18,2)    | Valor total de descontos aplicados                                        | —                      |
| invoice                      | VARCHAR(50)      | Número da nota fiscal da venda                                            | —                      |
| marketplace                  | VARCHAR(50)      | Canal de origem da venda                                                  | —                      |
| median_charged_shipping      | DECIMAL(18,2)    | Valor mediano de frete cobrado                                            | —                      |
| order_status_id              | INTEGER          | Código do status do pedido                                                | —                      |
| order_subtotal               | DECIMAL(18,2)    | Valor dos produtos sem impostos e frete                                   | —                      |
| order_total                  | DECIMAL(18,2)    | Valor total do pedido                                                     | —                      |
| order_type_id                | INTEGER          | Tipo de pedido (venda, devolução, etc.)                                   | —                      |
| partner_id                   | INTEGER          | Identificador do parceiro comercial                                       | —                      |
| partner_order_id             | VARCHAR(50)      | Código do pedido no sistema parceiro                                      | —                      |
| payment_method_id            | INTEGER          | Método de pagamento utilizado                                             | —                      |
| quantity                     | INTEGER          | Quantidade total de itens vendidos                                        | —                      |
| salesperson_account_id       | INTEGER          | Conta do vendedor responsável                                             | Chave Estrangeira      |
| salesperson_document         | VARCHAR(20)      | CPF ou CNPJ do vendedor responsável                                       | —                      |
| shipping_type_id             | INTEGER          | Tipo de envio associado à entrega                                         | —                      |
| site_id                      | INTEGER          | Canal ou ambiente de origem                                               | —                      |
| sku_id                       | INTEGER          | Identificador do produto (SKU)                                            | Chave Estrangeira      |
| unit_price                   | DECIMAL(18,2)    | Valor unitário do item vendido                                            | —                      |

---

## 👥 Tabela: `dClientes`

**Descrição Geral**  
Dimensão que consolida informações cadastrais, financeiras, geográficas e de relacionamento dos clientes.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_age_days             | INTEGER          | Dias de existência da conta do cliente                                    | —                      |
| account_create_date          | DATE             | Data de criação da conta do cliente                                       | —                      |
| account_id                   | INTEGER          | Identificador único da conta do cliente                                   | Chave Primária         |
| account_origin               | VARCHAR(50)      | Canal de origem do cadastro                                               | —                      |
| account_user                 | VARCHAR(150)     | Usuário ou e-mail do cliente                                              | —                      |
| age                          | INTEGER          | Idade do cliente                                                          | —                      |
| city                         | VARCHAR(100)     | Cidade do cliente                                                         | —                      |
| client_create_date           | DATE             | Data de criação do cliente                                                | —                      |
| client_id                    | INTEGER          | Código identificador do cliente                                           | Chave Primária         |
| client_last_updated          | DATE             | Data da última atualização                                                | —                      |
| client_status                | VARCHAR(20)      | Status atual do cliente                                                   | —                      |
| CNAE                         | VARCHAR(15)      | Código de atividade econômica                                             | —                      |
| contact                      | VARCHAR(150)     | Nome do contato principal                                                 | —                      |
| country                      | VARCHAR(50)      | País do cliente                                                           | —                      |
| credit_balance               | DECIMAL(18,2)    | Saldo atual de crédito                                                    | —                      |
| credit_limit                 | DECIMAL(18,2)    | Limite total de crédito concedido                                         | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | Chave Estrangeira      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do cliente                                                    | —                      |
| gender                       | VARCHAR(20)      | Gênero (quando aplicável)                                                 | —                      |
| line                         | VARCHAR(50)      | Linha comercial ou categoria                                              | —                      |
| name                         | VARCHAR(150)     | Nome completo ou razão social                                             | —                      |
| person_type                  | VARCHAR(10)      | Tipo de pessoa (PF/PJ)                                                    | —                      |
| phone_number                 | VARCHAR(20)      | Telefone principal                                                        | —                      |
| region                       | VARCHAR(30)      | Região geográfica derivada                                                | —                      |
| salesperson_account_id       | INTEGER          | Identificador do vendedor responsável                                     | Chave Estrangeira      |
| salesperson_document         | VARCHAR(20)      | Documento do vendedor responsável                                         | —                      |
| segment_description          | VARCHAR(100)     | Descrição do segmento de atuação                                          | —                      |
| site_id                      | INTEGER          | Canal ou ambiente de cadastro                                             | —                      |
| state                        | VARCHAR(50)      | Estado do cliente                                                         | —                      |
| total_credit_limit           | DECIMAL(18,2)    | Limite total de crédito do cliente                                        | —                      |
| UF                           | VARCHAR(5)       | Unidade Federativa                                                        | —                      |
| zip_code                     | VARCHAR(15)      | Código postal (CEP)                                                       | —                      |

---

## 🤝 Tabela: `dAssociados`

**Descrição Geral**  
Dimensão que reúne informações sobre parceiros comerciais, distribuidores, transportadoras e outras entidades associadas.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| city                         | VARCHAR(100)     | Cidade principal de localização do parceiro                               | —                      |
| company_name                 | VARCHAR(150)     | Razão social completa                                                     | —                      |
| copartner_id                 | INTEGER          | Identificador único do parceiro comercial                                 | Chave Primária         |
| correios                     | BOOLEAN          | Indica uso de serviço dos Correios                                        | —                      |
| country                      | VARCHAR(50)      | País de operação                                                          | —                      |
| cupon_habilitado             | BOOLEAN          | Indica se o parceiro aceita cupons                                        | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | Chave Estrangeira      |
| document                     | VARCHAR(20)      | CNPJ ou CPF do parceiro                                                   | —                      |
| ecommerce_habilitado         | BOOLEAN          | Indica integração com e-commerce                                          | —                      |
| entrega_economica            | BOOLEAN          | Indica oferta de frete econômico                                          | —                      |
| estados_b2b                  | VARCHAR(255)     | Estados com operação B2B                                                  | —                      |
| estados_b2c                  | VARCHAR(255)     | Estados com operação B2C                                                  | —                      |
| frota_propria                | BOOLEAN          | Indica frota logística própria                                            | —                      |
| last_update_date             | DATE             | Data da última atualização cadastral                                      | —                      |
| loggi                        | BOOLEAN          | Integração com Loggi                                                      | —                      |
| loja_configurada             | BOOLEAN          | Loja ou hub configurado                                                   | —                      |
| melhor_envio                 | BOOLEAN          | Integração com serviço Melhor Envio                                       | —                      |
| partner                      | VARCHAR(150)     | Nome comercial do parceiro                                                | —                      |
| partner_type                 | VARCHAR(50)      | Tipo de parceiro (distribuidor, transportadora, etc.)                     | —                      |
| partnership_date             | DATE             | Data de início da parceria                                                | —                      |
| plataform_status             | VARCHAR(30)      | Status da integração ou vínculo                                           | —                      |
| retirada_loja                | BOOLEAN          | Indica se há opção de retirada em loja                                    | —                      |
| state                        | VARCHAR(50)      | Estado de localização                                                     | —                      |
| street_address               | VARCHAR(255)     | Endereço completo                                                         | —                      |
| trading_name                 | VARCHAR(100)     | Nome fantasia do parceiro                                                 | —                      |
| trading_name_cut1            | VARCHAR(50)      | Nome fantasia abreviado                                                   | —                      |
| transportadoras              | VARCHAR(255)     | Transportadoras associadas                                                | —                      |
| uf                           | VARCHAR(5)       | Unidade Federativa (sigla)                                                | —                      |
| wirecard                     | BOOLEAN          | Integração com sistema de pagamento Wirecard                              | —                      |
| zip_code                     | VARCHAR(15)      | Código postal (CEP)                                                       | —                      |

---

## 📅 Tabela: `dCalendario`

**Descrição Geral**  
Dimensão temporal fundamental. Cada linha representa uma data única, com atributos para análises em diferentes níveis.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| Ano                          | INTEGER          | Ano civil correspondente à data                                           | —                      |
| AnoFiscal                    | INTEGER          | Ano fiscal da organização                                                 | —                      |
| AnoMes                       | VARCHAR(10)      | Combinação de ano e mês (AAAAMM)                                          | —                      |
| AnoMes_Fechamento            | VARCHAR(10)      | Período de fechamento fiscal                                              | —                      |
| AnoMesDia                    | VARCHAR(15)      | Ano, mês e dia concatenados                                               | —                      |
| AnoSemana                    | INTEGER          | Número da semana no ano civil                                             | —                      |
| AnoTrimestre                 | VARCHAR(10)      | Combinação de ano e trimestre                                             | —                      |
| Data                         | DATE             | Data completa                                                             | —                      |
| datekey                      | INTEGER          | Chave primária de data (AAAAMMDD)                                         | Chave Primária         |
| Dia                          | INTEGER          | Dia do mês                                                                | —                      |
| Dia_Semana                   | INTEGER          | Dia da semana (1 a 7)                                                     | —                      |
| DiaÚtil                      | BOOLEAN          | Indica se é dia útil                                                      | —                      |
| Feriado                      | BOOLEAN          | Indica feriado nacional                                                   | —                      |
| Futuro                       | BOOLEAN          | Indica data futura                                                        | —                      |
| Hoje                         | BOOLEAN          | Indica a data atual                                                       | —                      |
| Mês                          | INTEGER          | Mês do ano (1 a 12)                                                       | —                      |
| Mês_Atual                    | BOOLEAN          | Indica se pertence ao mês atual                                           | —                      |
| Mês_Completo                 | VARCHAR(20)      | Nome completo do mês                                                      | —                      |
| Mês_Fiscal                   | INTEGER          | Mês conforme calendário fiscal                                            | —                      |
| Mês/Ano                      | VARCHAR(10)      | Combinação de mês e ano                                                   | —                      |
| Mês/Ano_Fechamento           | VARCHAR(10)      | Período de fechamento mensal                                              | —                      |
| MesNo                        | INTEGER          | Índice do mês no ano                                                      | —                      |
| Nome_Dia                     | VARCHAR(15)      | Nome completo do dia da semana                                            | —                      |
| Nome_Dia_abv                 | VARCHAR(5)       | Abreviação do nome do dia                                                 | —                      |
| Offset_Ano                   | INTEGER          | Diferença em anos em relação ao atual                                     | —                      |
| Offset_Dia                   | INTEGER          | Diferença em dias em relação ao atual                                     | —                      |
| Offset_Mês                   | INTEGER          | Diferença em meses em relação ao atual                                    | —                      |
| Offset_Semana                | INTEGER          | Diferença em semanas em relação ao atual                                  | —                      |
| Offset_Trimestre             | INTEGER          | Diferença em trimestres em relação ao atual                               | —                      |
| Semana_Ano                   | INTEGER          | Semana dentro do ano                                                      | —                      |
| Semana_Atual                 | BOOLEAN          | Indica semana atual                                                       | —                      |
| Semana_Completa              | VARCHAR(15)      | Descrição completa da semana                                              | —                      |
| Semana_Mês                   | INTEGER          | Semana dentro do mês                                                      | —                      |
| Semana/Ano                   | VARCHAR(15)      | Combinação textual semana/ano                                             | —                      |
| Trimestre                    | INTEGER          | Número do trimestre (1–4)                                                 | —                      |
| Trimestre_Complete           | VARCHAR(10)      | Nome completo do trimestre                                                | —                      |
| Trimestre_Fiscal             | INTEGER          | Trimestre conforme calendário fiscal                                      | —                      |
| Trimestre/Ano                | VARCHAR(10)      | Combinação textual de trimestre e ano                                     | —                      |

---

## 🗂️ Tabela: `dCarteirizacao`

**Descrição Geral**  
Registra o relacionamento direto entre clientes, vendedores e lojas.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| id_account_customer          | INTEGER          | Identificador único do cliente associado à carteira                       | Chave Estrangeira      |
| id_account_seller            | INTEGER          | Identificador do vendedor responsável pelo cliente                        | Chave Estrangeira      |
| id_store                     | INTEGER          | Identificador da loja ou unidade de atendimento                           | Chave Estrangeira      |

---

## 🎫 Tabela: `dCupons`

**Descrição Geral**  
Armazena informações sobre cupons promocionais.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| coupon_id                    | INTEGER          | Identificador único do cupom promocional                                  | Chave Primária         |
| code                         | VARCHAR(50)      | Código do cupom aplicado em vendas                                        | —                      |
| campaign                     | VARCHAR(150)     | Nome ou descrição da campanha promocional                                 | —                      |
| datekey_begin                | INTEGER          | Data inicial da validade do cupom (AAAAMMDD)                              | —                      |
| datekey_end                  | INTEGER          | Data final da validade do cupom (AAAAMMDD)                                | —                      |
| site_id                      | INTEGER          | Identificador do site ou canal de origem                                  | —                      |

---

## 📱 Tabela: `dDispositivos`

**Descrição Geral**  
Armazena informações sobre dispositivos utilizados por clientes e vendedores.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| device_id                    | INTEGER          | Identificador único do dispositivo                                        | Chave Primária         |
| device                       | VARCHAR(50)      | Categoria ou tipo de dispositivo utilizado                                | —                      |

---

## 🎉 Tabela: `dFeriados`

**Descrição Geral**  
Armazena informações de feriados e datas comemorativas.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| Data                         | DATE             | Data completa do feriado                                                  | Chave Primária         |
| Dia_Semana                   | VARCHAR(15)      | Nome do dia da semana correspondente                                      | —                      |
| Feriado                      | VARCHAR(100)     | Nome ou descrição do feriado                                              | —                      |

---

## 👥 Tabela: `dGrupo_Cliente`

**Descrição Geral**  
Centraliza informações sobre agrupamento e categorização dos clientes.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador único do cliente                                            | Chave Primária         |
| name                         | VARCHAR(150)     | Nome completo ou razão social                                             | —                      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do cliente                                                    | —                      |
| customer_type                | VARCHAR(50)      | Categoria do cliente (PF, PJ, etc.)                                       | —                      |
| site_id                      | INTEGER          | Canal de origem do cadastro                                               | Chave Estrangeira      |

---

## 💳 Tabela: `dMetodo_pagamento`

**Descrição Geral**  
Armazena os diferentes métodos de pagamento disponíveis.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| payment_method_id            | INTEGER          | Identificador único do método de pagamento                                | Chave Primária         |
| payment_method               | VARCHAR(100)     | Nome ou descrição do método de pagamento                                  | —                      |

---

## 🛍️ Tabela: `dOfertas`

**Descrição Geral**  
Centraliza informações sobre produtos ofertados.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| associate_id                 | INTEGER          | Identificador do associado responsável pela oferta                        | Chave Estrangeira      |
| partner_id                   | INTEGER          | Identificador do parceiro comercial                                       | Chave Estrangeira      |
| company_name                 | VARCHAR(150)     | Nome da empresa responsável pela oferta                                   | —                      |
| partner_part_code            | VARCHAR(50)      | Código do produto no sistema do parceiro                                  | —                      |
| mfr_part_code                | VARCHAR(50)      | Código original do fabricante do produto                                  | —                      |
| sku_id                       | INTEGER          | Identificador único do SKU do produto                                     | Chave Primária         |
| sku_name                     | VARCHAR(150)     | Nome ou descrição comercial do produto                                    | —                      |
| unit_price                   | DECIMAL(18,2)    | Preço unitário da oferta                                                  | —                      |
| quantity_available           | INTEGER          | Quantidade disponível em estoque                                          | —                      |
| by_request                   | BOOLEAN          | Indica se o item está disponível apenas sob solicitação                   | —                      |
| datekey                      | INTEGER          | Data de referência da oferta (AAAAMMDD)                                   | Chave Estrangeira      |
| sku_created_date             | DATE             | Data de criação do SKU                                                    | —                      |
| sku_last_updated             | DATE             | Data da última atualização do SKU                                         | —                      |

---

## 📊 Tabela: `dPeriodos`

**Descrição Geral**  
Armazena informações sobre períodos de análise temporal.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| Data                         | DATE             | Data de referência do período                                             | —                      |
| Ordem                        | INTEGER          | Sequência numérica para ordenação temporal                                | —                      |
| Período                      | VARCHAR(50)      | Nome ou descrição do período de análise                                   | Chave Primária         |

---

## 📦 Tabela: `dProdutos`

**Descrição Geral**  
Dimensão que concentra informações dos produtos comercializados.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| sku_id                       | INTEGER          | Identificador único do produto (SKU)                                      | Chave Primária         |
| sku_name                     | VARCHAR(150)     | Nome comercial ou descritivo do produto                                   | —                      |
| mfr_part_code                | VARCHAR(50)      | Código original do fabricante                                             | —                      |
| manufacturer                 | VARCHAR(100)     | Nome do fabricante responsável                                            | —                      |
| category_level_1             | VARCHAR(100)     | Categoria principal do produto                                            | —                      |
| category_level_2             | VARCHAR(100)     | Subcategoria intermediária                                                | —                      |
| category_level_3             | VARCHAR(100)     | Subnível de categorização                                                 | —                      |
| nivel                        | VARCHAR(20)      | Nível hierárquico ou tipo de produto                                      | —                      |

---

## 📋 Tabela: `dStatus_pedido`

**Descrição Geral**  
Contém os status possíveis de um pedido.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| order_status_id              | INTEGER          | Identificador único do status do pedido                                   | Chave Primária         |
| order_status                 | VARCHAR(100)     | Nome ou descrição textual do status                                       | —                      |

---

## 🚚 Tabela: `dTipo_envio`

**Descrição Geral**  
Armazena os diferentes tipos de envio utilizados.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| shipping_type_id             | INTEGER          | Identificador único do tipo de envio                                      | Chave Primária         |
| shipping_type                | VARCHAR(100)     | Nome ou descrição da modalidade de envio                                  | —                      |

---

## 📦 Tabela: `dTipo_pedido`

**Descrição Geral**  
Contém as classificações dos tipos de pedidos.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| order_type_id                | INTEGER          | Identificador único do tipo de pedido                                     | Chave Primária         |
| order_type                   | VARCHAR(100)     | Nome ou descrição do tipo de pedido                                       | —                      |

---

## 🔐 Tabela: `fLogins`

**Descrição Geral**  
Registra todos os eventos de login realizados pelos usuários.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador único do usuário                                            | Chave Primária         |
| account_type                 | VARCHAR(50)      | Tipo da conta (cliente, vendedor, etc.)                                   | —                      |
| account_user                 | VARCHAR(150)     | Usuário ou e-mail de acesso                                               | —                      |
| datekey                      | INTEGER          | Chave da data no formato AAAAMMDD                                         | —                      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do usuário                                                    | —                      |
| login_date                   | DATE             | Data e hora do login                                                      | —                      |
| login_type                   | VARCHAR(50)      | Tipo de autenticação utilizada                                            | —                      |
| site_id                      | INTEGER          | Identificador do site de origem                                           | —                      |

---

## 📈 Tabela: `fDatalayer_session_summary`

**Descrição Geral**  
Consolida dados de sessões de visitantes e usuários autenticados.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do usuário                                                  | Chave Primária         |
| datekey                      | INTEGER          | Data da sessão (AAAAMMDD)                                                 | —                      |
| session                      | VARCHAR(100)     | Código único da sessão                                                    | —                      |
| session_time_in_seconds      | INTEGER          | Tempo total da sessão em segundos                                         | —                      |
| site_id                      | INTEGER          | Identificador do site da sessão                                           | —                      |
| user_type                    | VARCHAR(50)      | Tipo de usuário                                                           | —                      |
| vendor_id                    | INTEGER          | Identificador do vendedor associado                                       | —                      |
| vendor_isloggedin            | BOOLEAN          | Status de login do vendedor                                               | —                      |
| visitor_id                   | INTEGER          | Identificador do visitante                                                | —                      |
| visitor_isloggedin           | BOOLEAN          | Status de login do visitante                                              | —                      |

---

## 👀 Tabela: `fDatalayer_product_pageviews`

**Descrição Geral**  
Armazena visualizações de página de produtos.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do usuário                                                  | Chave Primária         |
| datekey                      | INTEGER          | Data da visualização                                                      | —                      |
| datekey_max_datecreated      | INTEGER          | Data máxima de interação                                                  | —                      |
| datekey_min_datecreated      | INTEGER          | Data mínima de interação                                                  | —                      |
| distinct_count_session       | INTEGER          | Contagem de sessões únicas                                                | —                      |
| max_datecreated_time         | TIMESTAMP        | Horário da última visualização                                            | —                      |
| min_datecreated_time         | TIMESTAMP        | Horário da primeira visualização                                          | —                      |
| site_id                      | INTEGER          | Identificador do site                                                     | —                      |
| sku_id                       | INTEGER          | Código do produto visualizado                                             | Chave Estrangeira      |
| vendor_id                    | INTEGER          | Identificador do vendedor                                                 | —                      |
| vendor_email                 | VARCHAR(100)     | E-mail do vendedor                                                        | —                      |
| vendor_isloggedin            | BOOLEAN          | Status de login do vendedor                                               | —                      |
| visitor_id                   | INTEGER          | Identificador do visitante                                                | —                      |
| visitor_email                | VARCHAR(100)     | E-mail do visitante                                                       | —                      |
| visitor_isloggedin           | BOOLEAN          | Status de login do visitante                                              | —                      |

---

## 🛒 Tabela: `fCarrinhos_abandonados`

**Descrição Geral**  
Registra carrinhos de compras criados e não finalizados.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| cart_type                    | VARCHAR(50)      | Tipo de carrinho                                                          | —                      |
| client_account_id            | INTEGER          | Conta do cliente associado                                                | Chave Primária         |
| data                         | DATE             | Data de criação ou abandono                                               | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | —                      |
| device_id                    | VARCHAR(50)      | Identificador do dispositivo                                              | —                      |
| mfr_part_code                | VARCHAR(50)      | Código do fabricante                                                      | —                      |
| partner                      | VARCHAR(100)     | Nome do parceiro comercial                                                | —                      |
| quantity                     | INTEGER          | Quantidade de produtos                                                    | —                      |
| session_id                   | VARCHAR(100)     | Identificador da sessão                                                   | —                      |
| site_id                      | INTEGER          | Identificador do site                                                     | —                      |
| sku_id                       | INTEGER          | Código do produto (SKU)                                                   | Chave Estrangeira      |
| sku_name                     | VARCHAR(150)     | Nome do produto                                                           | —                      |
| unit_price                   | DECIMAL(18,2)    | Valor unitário do item                                                    | —                      |

---

## ⏱️ Tabela: `agg_last_login`

**Descrição Geral**  
Consolida informações do último login por usuário.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do usuário                                                  | Chave Primária         |
| days_since_last_login        | INTEGER          | Dias desde o último login                                                 | —                      |
| login_status                 | VARCHAR(20)      | Status do login                                                           | —                      |
| site_id                      | INTEGER          | Identificador do site                                                     | —                      |

---

## 🛍️ Tabela: `agg_last_purchase`

**Descrição Geral**  
Armazena informações sobre a última compra de cada cliente.

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do cliente                                                  | Chave Primária         |
| days_since_last_purchase     | INTEGER          | Dias desde a última compra                                                | —                      |
| plataform_status             | VARCHAR(50)      | Status da plataforma do cliente                                           | —                      |
| site_id                      | INTEGER          | Identificador do site de origem                                           | —                      |

---

Aqui estão as tabelas faltantes documentadas em Markdown:

---

## 🏪 Tabela: `dLojas`

**Descrição Geral**  
Dimensão que armazena informações sobre lojas, unidades de negócio e pontos de venda. Cada registro representa uma loja única com dados cadastrais, geográficos e operacionais.

| Nome da Coluna      | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|---------------------|--------------|------------------------------------------------|------------------------|
| store_id            | INTEGER      | Identificador único da loja                    | Chave Primária         |
| store_name          | VARCHAR(100) | Nome comercial da loja                         | —                      |
| trading_name        | VARCHAR(100) | Nome fantasia                                  | —                      |
| company_name        | VARCHAR(150) | Razão social completa                          | —                      |
| document            | VARCHAR(20)  | CNPJ da loja                                   | —                      |
| phone_number        | VARCHAR(20)  | Telefone de contato                            | —                      |
| email               | VARCHAR(100) | E-mail comercial                               | —                      |
| country             | VARCHAR(50)  | País de localização                            | —                      |
| UF                  | VARCHAR(5)   | Unidade Federativa                             | —                      |
| state               | VARCHAR(50)  | Estado completo                                | —                      |
| city                | VARCHAR(100) | Cidade                                         | —                      |
| zip_code            | VARCHAR(15)  | Código postal (CEP)                            | —                      |
| street_address      | VARCHAR(255) | Endereço completo                              | —                      |
| store_status        | VARCHAR(20)  | Status da loja (Ativa/Inativa)                 | —                      |
| store_type          | VARCHAR(50)  | Tipo de loja (Física/Virtual/Franquia)         | —                      |
| opening_date        | DATE         | Data de inauguração                            | —                      |
| closing_date        | DATE         | Data de fechamento (se aplicável)              | —                      |
| salesperson_account_id | INTEGER   | Vendedor responsável pela loja                 | Chave Estrangeira      |
| datekey             | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 🌐 Tabela: `dSites`

**Descrição Geral**  
Dimensão que cataloga todos os sites, plataformas digitais e canais de venda online. Essencial para análises de desempenho por canal digital.

| Nome da Coluna      | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|---------------------|--------------|------------------------------------------------|------------------------|
| site_id             | INTEGER      | Identificador único do site                    | Chave Primária         |
| site_name           | VARCHAR(100) | Nome do site/plataforma                        | —                      |
| site_url            | VARCHAR(255) | URL completa do site                           | —                      |
| site_type           | VARCHAR(50)  | Tipo de site (E-commerce, Marketplace, App)    | —                      |
| platform            | VARCHAR(50)  | Plataforma tecnológica                         | —                      |
| site_status         | VARCHAR(20)  | Status do site (Ativo/Inativo/Manutenção)      | —                      |
| launch_date         | DATE         | Data de lançamento do site                     | —                      |
| country             | VARCHAR(50)  | País de operação do site                       | —                      |
| default_currency    | VARCHAR(10)  | Moeda padrão do site                           | —                      |
| default_language    | VARCHAR(10)  | Idioma padrão do site                          | —                      |
| timezone            | VARCHAR(50)  | Fuso horário do site                           | —                      |
| datekey             | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 🏭 Tabela: `dFabricantes`

**Descrição Geral**  
Dimensão que armazena informações sobre fabricantes e marcas dos produtos comercializados. Fundamental para análises por marca e fornecedor.

| Nome da Coluna      | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|---------------------|--------------|------------------------------------------------|------------------------|
| manufacturer_id     | INTEGER      | Identificador único do fabricante              | Chave Primária         |
| manufacturer_name   | VARCHAR(100) | Nome do fabricante                             | —                      |
| manufacturer_code   | VARCHAR(50)  | Código interno do fabricante                   | —                      |
| document            | VARCHAR(20)  | CNPJ do fabricante                             | —                      |
| country             | VARCHAR(50)  | País de origem                                 | —                      |
| contact_name        | VARCHAR(150) | Nome do contato principal                      | —                      |
| contact_email       | VARCHAR(100) | E-mail de contato                              | —                      |
| contact_phone       | VARCHAR(20)  | Telefone de contato                            | —                      |
| manufacturer_status | VARCHAR(20)  | Status do fabricante (Ativo/Inativo)           | —                      |
| partnership_date    | DATE         | Data de início da parceria                     | —                      |
| datekey             | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 📂 Tabela: `dCategorias`

**Descrição Geral**  
Dimensão que define a hierarquia de categorização de produtos. Suporta estrutura multi-nível para organização do catálogo.

| Nome da Coluna      | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|---------------------|--------------|------------------------------------------------|------------------------|
| category_id         | INTEGER      | Identificador único da categoria               | Chave Primária         |
| category_name       | VARCHAR(100) | Nome da categoria                              | —                      |
| category_level      | INTEGER      | Nível hierárquico (1, 2, 3)                   | —                      |
| parent_category_id  | INTEGER      | ID da categoria pai (para subcategorias)       | Chave Estrangeira      |
| category_path       | VARCHAR(255) | Caminho completo da categoria                  | —                      |
| category_description| VARCHAR(255) | Descrição da categoria                         | —                      |
| category_status     | VARCHAR(20)  | Status da categoria (Ativa/Inativa)            | —                      |
| datekey             | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 💰 Tabela: `fVendas`

**Descrição Geral**  
Tabela fato principal que registra todas as transações de vendas. Cada linha representa um item de pedido vendido, com informações financeiras, quantitativas e de relacionamento.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| sales_id                | INTEGER      | Identificador único da venda                   | Chave Primária         |
| order_id                | INTEGER      | Número do pedido                               | —                      |
| order_item_id           | INTEGER      | Identificador do item no pedido                | —                      |
| datekey                 | INTEGER      | Data da venda (AAAAMMDD)                       | Chave Estrangeira      |
| datekey_faturamento     | INTEGER      | Data de faturamento (AAAAMMDD)                 | Chave Estrangeira      |
| client_account_id       | INTEGER      | Cliente comprador                              | Chave Estrangeira      |
| salesperson_account_id  | INTEGER      | Vendedor responsável                           | Chave Estrangeira      |
| store_id                | INTEGER      | Loja/unidade de venda                          | Chave Estrangeira      |
| site_id                 | INTEGER      | Site/canal de origem                           | Chave Estrangeira      |
| sku_id                  | INTEGER      | Produto vendido                                | Chave Estrangeira      |
| quantity                | INTEGER      | Quantidade vendida                             | —                      |
| unit_price              | DECIMAL(18,2)| Preço unitário                                 | —                      |
| total_amount            | DECIMAL(18,2)| Valor total do item                            | —                      |
| discount_value          | DECIMAL(18,2)| Valor de desconto aplicado                     | —                      |
| tax_amount              | DECIMAL(18,2)| Valor de impostos                              | —                      |
| shipping_amount         | DECIMAL(18,2)| Valor do frete                                 | —                      |
| net_amount              | DECIMAL(18,2)| Valor líquido da venda                         | —                      |
| payment_method_id       | INTEGER      | Método de pagamento                            | Chave Estrangeira      |
| order_status_id         | INTEGER      | Status do pedido                               | Chave Estrangeira      |
| order_type_id           | INTEGER      | Tipo do pedido                                 | Chave Estrangeira      |
| shipping_type_id        | INTEGER      | Tipo de envio                                  | Chave Estrangeira      |
| coupon_id               | INTEGER      | Cupom aplicado                                 | Chave Estrangeira      |
| invoice_number          | VARCHAR(50)  | Número da nota fiscal                          | —                      |
| device_id               | INTEGER      | Dispositivo utilizado                          | Chave Estrangeira      |

---

## 🚚 Tabela: `fEntregas`

**Descrição Geral**  
Tabela fato que registra informações sobre o processo de entrega dos pedidos. Acompanha todo o ciclo logístico desde a expedição até a entrega ao cliente.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| delivery_id             | INTEGER      | Identificador único da entrega                 | Chave Primária         |
| sales_id                | INTEGER      | Venda associada                                | Chave Estrangeira      |
| order_id                | INTEGER      | Número do pedido                               | —                      |
| datekey_expedicao       | INTEGER      | Data de expedição (AAAAMMDD)                   | Chave Estrangeira      |
| datekey_entrega         | INTEGER      | Data de entrega (AAAAMMDD)                     | Chave Estrangeira      |
| client_account_id       | INTEGER      | Cliente destinatário                           | Chave Estrangeira      |
| shipping_type_id        | INTEGER      | Tipo de envio                                  | Chave Estrangeira      |
| carrier_id              | INTEGER      | Transportadora                                 | Chave Estrangeira      |
| tracking_number         | VARCHAR(100) | Código de rastreamento                         | —                      |
| shipping_status         | VARCHAR(30)  | Status da entrega                              | —                      |
| expected_days           | INTEGER      | Prazo esperado de entrega (dias)               | —                      |
| actual_days             | INTEGER      | Prazo real de entrega (dias)                   | —                      |
| shipping_cost           | DECIMAL(18,2)| Custo do frete                                 | —                      |
| shipping_charged        | DECIMAL(18,2)| Valor cobrado pelo frete                       | —                      |
| delivery_address        | VARCHAR(255) | Endereço de entrega                            | —                      |
| delivery_city           | VARCHAR(100) | Cidade de entrega                              | —                      |
| delivery_UF             | VARCHAR(5)   | UF de entrega                                  | —                      |
| delivery_zip_code       | VARCHAR(15)  | CEP de entrega                                 | —                      |
| recipient_name          | VARCHAR(150) | Nome do destinatário                           | —                      |
| recipient_document      | VARCHAR(20)  | CPF/CNPJ do destinatário                       | —                      |

---

## 🔄 Tabelas de Relacionamento Adicionais:

### `produto_categoria` (Tabela Ponte)
**Descrição Geral:** Relacionamento muitos-para-muitos entre produtos e categorias.

| Nome da Coluna      | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|---------------------|--------------|------------------------------------------------|------------------------|
| sku_id              | INTEGER      | Identificador do produto                       | Chave Estrangeira      |
| category_id         | INTEGER      | Identificador da categoria                     | Chave Estrangeira      |
| datekey             | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

### `vendedor_loja` (Tabela Ponte)
**Descrição Geral:** Relacionamento entre vendedores e lojas que atendem.

| Nome da Coluna      | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|---------------------|--------------|------------------------------------------------|------------------------|
| salesperson_account_id | INTEGER   | Identificador do vendedor                      | Chave Estrangeira      |
| store_id            | INTEGER      | Identificador da loja                          | Chave Estrangeira      |
| datekey             | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

Você está absolutamente certo! Analisando novamente o documento original, identifiquei que **ainda faltam tabelas** que estão mencionadas no PDF mas não foram documentadas. Vou adicionar as que estão faltando:

---

## 🏪 Tabela: `dLojas`

**Descrição Geral**  
Dimensão que armazena informações sobre lojas, unidades de negócio e pontos de venda. Cada registro representa uma loja única.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| store_id                | INTEGER      | Identificador único da loja                    | Chave Primária         |
| store_name              | VARCHAR(100) | Nome comercial da loja                         | —                      |
| store_type              | VARCHAR(50)  | Tipo de loja (Física/Virtual)                  | —                      |
| store_status            | VARCHAR(20)  | Status da loja (Ativa/Inativa)                 | —                      |
| phone_number            | VARCHAR(20)  | Telefone de contato                            | —                      |
| email                   | VARCHAR(100) | E-mail comercial                               | —                      |
| country                 | VARCHAR(50)  | País de localização                            | —                      |
| UF                      | VARCHAR(5)   | Unidade Federativa                             | —                      |
| state                   | VARCHAR(50)  | Estado completo                                | —                      |
| city                    | VARCHAR(100) | Cidade                                         | —                      |
| zip_code                | VARCHAR(15)  | Código postal (CEP)                            | —                      |
| street_address          | VARCHAR(255) | Endereço completo                              | —                      |
| opening_date            | DATE         | Data de inauguração                            | —                      |
| salesperson_account_id  | INTEGER      | Vendedor responsável pela loja                 | Chave Estrangeira      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 🏷️ Tabela: `dSegmentacao` (Implícita)

**Descrição Geral**  
Dimensão que define os segmentos comerciais e categorizações utilizadas para clientes e vendedores.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| segment_id              | INTEGER      | Identificador único do segmento                | Chave Primária         |
| segment_code            | VARCHAR(10)  | Código do segmento (ex.: M1, Q4)              | —                      |
| segment_description     | VARCHAR(100) | Descrição textual do segmento                  | —                      |
| segment_type            | VARCHAR(50)  | Tipo de segmentação (Cliente/Vendedor)         | —                      |
| criteria                | VARCHAR(255) | Critérios de segmentação                       | —                      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 🏗️ Tabela: `dEstrutura_Comercial` (Implícita)

**Descrição Geral**  
Dimensão que define a estrutura hierárquica comercial da organização (divisões, regiões, áreas).

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| structure_id            | INTEGER      | Identificador único da estrutura               | Chave Primária         |
| division                | VARCHAR(30)  | Divisão comercial (ex.: AUTO, METAL)           | —                      |
| region                  | VARCHAR(30)  | Região geográfica                              | —                      |
| area                    | VARCHAR(50)  | Área comercial                                 | —                      |
| hierarchy_level         | INTEGER      | Nível hierárquico                              | —                      |
| parent_structure_id     | INTEGER      | ID da estrutura pai                            | Chave Estrangeira      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 📦 Tabela: `dTransportadoras`

**Descrição Geral**  
Dimensão que armazena informações sobre transportadoras e serviços de entrega.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| carrier_id              | INTEGER      | Identificador único da transportadora          | Chave Primária         |
| carrier_name            | VARCHAR(100) | Nome da transportadora                         | —                      |
| carrier_type            | VARCHAR(50)  | Tipo de serviço (Expresso, Econômico)          | —                      |
| document                | VARCHAR(20)  | CNPJ da transportadora                         | —                      |
| contact_phone           | VARCHAR(20)  | Telefone de contato                            | —                      |
| service_level           | VARCHAR(30)  | Nível de serviço                               | —                      |
| coverage_area           | VARCHAR(255) | Área de cobertura                              | —                      |
| carrier_status          | VARCHAR(20)  | Status da transportadora                       | —                      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 🎯 Tabela: `dCampanhas`

**Descrição Geral**  
Dimensão que armazena informações sobre campanhas de marketing e promoções.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| campaign_id             | INTEGER      | Identificador único da campanha                | Chave Primária         |
| campaign_name           | VARCHAR(150) | Nome da campanha                               | —                      |
| campaign_type           | VARCHAR(50)  | Tipo de campanha                               | —                      |
| start_date              | DATE         | Data de início                                 | —                      |
| end_date                | DATE         | Data de término                                | —                      |
| target_audience         | VARCHAR(100) | Público-alvo                                   | —                      |
| budget                  | DECIMAL(18,2)| Orçamento da campanha                          | —                      |
| campaign_status         | VARCHAR(20)  | Status da campanha                             | —                      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 🔄 Tabela: `fVendas_Detalhadas` (Alternativa à Ólendas)

**Descrição Geral**  
Tabela fato alternativa/detalhada para transações de vendas com granularidade adicional.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| sales_detail_id         | INTEGER      | Identificador único do detalhe                 | Chave Primária         |
| sales_id                | INTEGER      | ID da venda principal                          | Chave Estrangeira      |
| sku_id                  | INTEGER      | Produto vendido                                | Chave Estrangeira      |
| quantity                | INTEGER      | Quantidade vendida                             | —                      |
| unit_price              | DECIMAL(18,2)| Preço unitário                                 | —                      |
| discount_value          | DECIMAL(18,2)| Valor de desconto                              | —                      |
| tax_amount              | DECIMAL(18,2)| Valor de impostos                              | —                      |
| line_total              | DECIMAL(18,2)| Total da linha                                 | —                      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

## 📊 Tabela: `fMetas`

**Descrição Geral**  
Tabela fato que armazena metas e objetivos comerciais por vendedor, equipe ou região.

| Nome da Coluna          | Tipo de Dado | Descrição                                      | Chave / Relacionamento |
|-------------------------|--------------|------------------------------------------------|------------------------|
| goal_id                 | INTEGER      | Identificador único da meta                    | Chave Primária         |
| account_id              | INTEGER      | Vendedor/equipe                                | Chave Estrangeira      |
| goal_type               | VARCHAR(50)  | Tipo de meta (Vendas, Clientes)                | —                      |
| target_value            | DECIMAL(18,2)| Valor da meta                                  | —                      |
| actual_value            | DECIMAL(18,2)| Valor realizado                                | —                      |
| goal_period             | VARCHAR(20)  | Período da meta (Mensal, Trimestral)           | —                      |
| start_date              | DATE         | Data de início                                 | —                      |
| end_date                | DATE         | Data de término                                | —                      |
| datekey                 | INTEGER      | Chave temporal (AAAAMMDD)                      | Chave Estrangeira      |

---

