# Porto Baré — Parte 1: Negócio e Requisitos

| | |
|---|---|
| **Instituição** | Centro Universitário de Ensino Superior do Amazonas (CIESA) |
| **Curso** | Análise e Desenvolvimento de Sistemas (ADS) |
| **Disciplina** | Projetos de Sistemas |
| **Trabalho** | Requisitos e Arquitetura de um Sistema   |
| **Aluno** | José Lima da Mota Neto - 25000360 |
| **Professor** | Brendo Rodrigo Souza de Matos |
| **Sistema** | Porto Baré — consulta e agendamento de embarcações |
| **Versão** | 1.0 — Parte 1 (Negócio e Requisitos) — novembro de 2026 |

> A Parte 2 (documento de arquitetura) será entregue em etapa posterior e usará os códigos de requisitos deste documento como base de rastreabilidade.

---

## Sumário

1. [Introdução](#1-introdução)
2. [Descrição do sistema](#2-descrição-do-sistema)
3. [Requisitos funcionais (RF)](#3-requisitos-funcionais-rf)
4. [Requisitos não funcionais (RNF)](#4-requisitos-não-funcionais-rnf)
5. [Regras de negócio (RN)](#5-regras-de-negócio-rn)
6. [Visão consolidada e conformidade com o enunciado](#6-visão-consolidada-e-conformidade-com-o-enunciado)

---

## 1. Introdução

Este documento apresenta o negócio e o levantamento de requisitos do **Porto Baré**, sistema fictício de consulta e agendamento de embarcações em Manaus. O foco é conceitual: não há programação, e o objetivo é classificar corretamente os requisitos em três tipos.

| Tipo | Código | O que descreve |
|---|---|---|
| Requisito funcional | RF01, RF02… | O que o sistema **faz** para cada usuário. |
| Requisito não funcional | RNF01, RNF02… | **Como** o sistema se comporta (desempenho, segurança, etc.), sempre com uma medida verificável. |
| Regra de negócio | RN01, RN02… | Regra do negócio que **valeria mesmo sem o sistema** (lei, norma ou política da empresa). |

**Prioridades:** *Alta* é o requisito essencial ao funcionamento ou à segurança das pessoas, *Média* é importante mas o sistema opera sem ele por um período, e *Baixa* é desejável e pode ser entregue depois.

---

## 2. Descrição do sistema

O **Porto Baré** é um sistema web e mobile que reúne, em um só lugar, a oferta de embarcações de Manaus (barcos, lanchas, jet skis, balsas, voadeiras e outras) para passeio, aluguel ou transporte fluvial. Nele, **clientes** consultam as embarcações disponíveis, conferem a ficha técnica, a licença, o seguro e a garantia, agendam e pagam o serviço; **proprietários** (pessoas físicas ou empresas náuticas) cadastram suas embarcações, controlam a agenda e respondem às solicitações; e o **administrador** valida a documentação, monitora vencimentos, trata ocorrências e acompanha os resultados. O sistema tem como princípio a **transparência** para os dois lados: o cliente contrata sabendo exatamente o que está contratando, e o proprietário mantém seus dados e documentos atualizados e rastreáveis.

### 2.1 Perfis de usuário

| Perfil | Quem é | Principais requisitos funcionais |
|---|---|---|
| Cliente | Pessoa que quer consultar, agendar e usar uma embarcação. | RF01 a RF08, RF17, RF18, RF19, RF21, RF23 |
| Proprietário | Pessoa física ou empresa náutica dona ou responsável pela embarcação. | RF09, RF10, RF11, RF14, RF15, RF16, RF21, RF22, RF23 |
| Administrador | Equipe interna do Porto Baré que valida e supervisiona. | RF12, RF13, RF20 |

### 2.2 Fluxo de negócio resumido

1. O proprietário se cadastra e registra a embarcação, com ficha técnica, documentos, licença e seguro.
2. O administrador confere a documentação e aprova ou rejeita o cadastro.
3. O cliente consulta as embarcações aprovadas, filtra e analisa a ficha completa.
4. O cliente solicita o agendamento e revê o resumo (preço, taxas, política de cancelamento, termo de responsabilidade).
5. O proprietário aceita ou recusa a solicitação; o cliente paga o agendamento aceito.
6. Ocorre o passeio, com acesso ao botão de emergência durante todo o trajeto.
7. O cliente avalia o serviço, e eventuais ocorrências ou reclamações são registradas e tratadas.

### 2.3 Escopo e premissas

**Dentro do escopo:** consulta, agendamento, pagamento, transparência de dados e documentos da embarcação, segurança e emergência, gestão e relatórios.

**Fora do escopo:** rastreamento contínuo da embarcação em tempo real, transporte de cargas e implementação de código.

**Premissas:**

- O Porto Baré atua como **plataforma intermediadora** entre clientes e proprietários, com atuação inicial em Manaus e região.
- O pagamento é feito por **gateway de pagamento externo**, e o sistema não armazena dados de cartão.
- Contas de administrador são criadas internamente pela equipe do Porto Baré.
- Exigências legais (documentação, habilitação, equipamentos de segurança) seguem as normas vigentes da Autoridade Marítima (Marinha do Brasil). O sistema registra e acompanha a validade dos documentos, mas não substitui a fiscalização oficial.
- Valores e prazos de políticas comerciais (como a do RN06) são definidos pelo Porto Baré e podem ser ajustados.

---

## 3. Requisitos funcionais (RF)

| Código | Usuário | Descrição | Prioridade |
|---|---|---|---|
| RF01 | Cliente | O sistema deve permitir que o cliente se cadastre e faça login. | Alta |
| RF02 | Cliente | O sistema deve permitir que o cliente consulte embarcações disponíveis filtrando por tipo, capacidade, data, preço e porto de saída. | Alta |
| RF03 | Cliente | O sistema deve permitir que o cliente visualize os detalhes de uma embarcação (fotos, capacidade, equipamentos de segurança e avaliações). | Média |
| RF04 | Cliente | O sistema deve permitir que o cliente agende uma embarcação informando data, horário e número de passageiros. | Alta |
| RF05 | Cliente | O sistema deve permitir que o cliente pague o agendamento online. | Alta |
| RF06 | Cliente | O sistema deve permitir que o cliente cancele ou reagende um agendamento. | Média |
| RF07 | Cliente | O sistema deve permitir que o cliente avalie a embarcação e o serviço após o passeio. | Baixa |
| RF08 | Cliente | O sistema deve permitir que o cliente consulte o histórico dos seus agendamentos. | Baixa |
| RF09 | Proprietário | O sistema deve permitir que o proprietário cadastre uma embarcação com tipo, capacidade, preço e fotos. | Alta |
| RF10 | Proprietário | O sistema deve permitir que o proprietário gerencie o calendário de disponibilidade das suas embarcações. | Alta |
| RF11 | Proprietário | O sistema deve permitir que o proprietário aceite ou recuse solicitações de agendamento. | Média |
| RF12 | Administrador | O sistema deve permitir que o administrador aprove ou rejeite o cadastro de embarcações após conferir a documentação. | Alta |
| RF13 | Administrador | O sistema deve permitir que o administrador gere relatórios de agendamentos e receitas por período. | Baixa |
| RF14 | Proprietário | O sistema deve permitir que o proprietário registre a ficha técnica da embarcação: nome, marca, modelo, ano de fabricação, motor (tipo, potência e quantidade), número de inscrição, capacidade e equipamentos de segurança (coletes, extintor, boias e kit de primeiros socorros). | Alta |
| RF15 | Proprietário | O sistema deve permitir que o proprietário informe seus dados (razão social ou nome, CNPJ ou CPF e contato) e envie a licença e os documentos da embarcação e a habilitação do condutor, com data de validade. | Alta |
| RF16 | Proprietário | O sistema deve permitir que o proprietário informe o seguro (seguradora, apólice, cobertura e validade) e as condições de garantia do serviço. | Alta |
| RF17 | Cliente | O sistema deve permitir que o cliente visualize a ficha técnica, a licença, o seguro e a garantia da embarcação antes de agendar. | Alta |
| RF18 | Cliente | O sistema deve permitir que o cliente veja, antes de confirmar o agendamento, o resumo com preço total, taxas, política de cancelamento e termo de responsabilidade, e registre o aceite. | Alta |
| RF19 | Cliente | O sistema deve permitir que o cliente acione um botão de emergência durante o passeio, que envia sua localização e exibe os contatos de emergência (Bombeiros 193, SAMU 192 e Marinha 185). | Alta |
| RF20 | Administrador | O sistema deve permitir que o administrador visualize as embarcações com documentos ou seguro vencidos ou a vencer e as suspenda. | Média |
| RF21 | Cliente e proprietário | O sistema deve permitir que o cliente ou o proprietário registre uma ocorrência ou reclamação de segurança sobre uma embarcação ou passeio. | Média |
| RF22 | Proprietário | O sistema deve permitir que o proprietário se cadastre e faça login. | Alta |
| RF23 | Cliente e proprietário | O sistema deve permitir que o cliente e o proprietário recebam notificações por e-mail ou aplicativo sobre solicitação, aceite, recusa, cancelamento e lembrete do passeio. | Média |

---

## 4. Requisitos não funcionais (RNF)

| Código | Categoria | Descrição | Medida | Prioridade |
|---|---|---|---|---|
| RNF01 | Desempenho | A consulta de embarcações com filtros deve retornar resultados em até 2 segundos para 95% das requisições, com até 500 usuários simultâneos. | 2 s, 95%, 500 usuários | Alta |
| RNF02 | Desempenho | O registro de uma solicitação de agendamento deve ser concluído em até 3 segundos no horário de pico. | 3 s | Alta |
| RNF03 | Desempenho | A página inicial deve carregar em até 4 segundos em conexão móvel 3G. | 4 s em 3G | Média |
| RNF04 | Segurança | 100% das comunicações entre cliente e servidor devem usar HTTPS (TLS 1.2 ou superior), e as senhas devem ser armazenadas com hash. | 100% HTTPS, TLS ≥ 1.2 | Alta |
| RNF05 | Segurança | O sistema deve tratar os dados pessoais conforme a LGPD (Lei 13.709/2018) e encerrar a sessão após 15 minutos de inatividade. | Lei 13.709/2018, 15 min | Alta |
| RNF06 | Disponibilidade | O sistema deve ter disponibilidade mínima de 99% ao mês (no máximo cerca de 7 horas de indisponibilidade em 30 dias). | 99% ao mês | Alta |
| RNF07 | Usabilidade e acessibilidade | Um usuário novo deve concluir um agendamento em até 5 minutos, sem treinamento, e as telas devem seguir o nível AA da WCAG 2.1. | 5 min, WCAG 2.1 AA | Média |
| RNF08 | Compatibilidade | O sistema deve funcionar nas 2 últimas versões do Chrome, Firefox, Edge e Safari e em telas a partir de 360 px de largura. | 2 versões, 4 navegadores, 360 px | Média |
| RNF09 | Segurança | O sistema deve registrar em log de auditoria 100% das alterações em dados de embarcação, documentos e seguro, com data, hora e usuário, mantendo o histórico por no mínimo 12 meses. | 100%, 12 meses | Média |
| RNF10 | Desempenho | O alerta de emergência deve ser enviado, com a localização, em até 5 segundos após o acionamento do botão. | 5 s | Alta |
| RNF11 | Usabilidade e acessibilidade | A ficha da embarcação e o botão de emergência devem estar acessíveis em até 2 toques a partir de qualquer tela. | 2 toques | Média |
| RNF12 | Segurança | Os documentos enviados (licença, apólice, habilitação) devem ser armazenados criptografados (AES-256) e acessíveis apenas ao próprio usuário e ao administrador. | AES-256 | Alta |

---

## 5. Regras de negócio (RN)

| Código | Tema | Descrição | Prioridade |
|---|---|---|---|
| RN01 | Documentação | Toda embarcação só pode operar com a documentação regularizada junto à Autoridade Marítima (Marinha do Brasil). | Alta |
| RN02 | Capacidade | O número de passageiros não pode exceder a capacidade máxima da embarcação. | Alta |
| RN03 | Segurança | Todo passageiro deve usar colete salva-vidas, e a embarcação deve ter um colete para cada ocupante. | Alta |
| RN04 | Habilitação | O jet ski só pode ser conduzido por pessoa habilitada pela Marinha. | Alta |
| RN05 | Menores | Menores de 18 anos só podem embarcar acompanhados de um responsável. | Média |
| RN06 | Cancelamento | Cancelamentos feitos com 24 horas ou mais de antecedência têm reembolso integral. Depois disso, retém-se 30% do valor. | Média |
| RN07 | Clima | Passeios podem ser suspensos em caso de condições climáticas adversas (tempestade, vento forte), com remarcação sem custo. | Média |
| RN08 | Seguro | Toda embarcação só pode ser oferecida ao público com seguro vigente que cubra os passageiros. | Alta |
| RN09 | Responsabilidade | O proprietário é responsável pela segurança dos passageiros, pela condição da embarcação e pela condução durante todo o passeio. | Alta |
| RN10 | Equipamentos | A embarcação deve manter em condições de uso os equipamentos obrigatórios de segurança (extintor, boias, sinalização e kit de primeiros socorros) e a vistoria em dia. | Alta |
| RN11 | Informação | O fornecedor deve informar de forma clara e verdadeira as características, o preço e os riscos do serviço (direito à informação do Código de Defesa do Consumidor). | Alta |
| RN12 | Emergência | Em caso de acidente ou emergência, o condutor deve prestar socorro e comunicar o fato à Autoridade Marítima. | Alta |
| RN13 | Garantia | Se o passeio não ocorrer por pane ou defeito da embarcação, o cliente tem direito a remarcação ou reembolso proporcional. | Média |

---

## 6. Visão consolidada e conformidade com o enunciado

### 6.1 Resumo quantitativo

| Tipo | Mínimo exigido | Entregue | Alta | Média | Baixa |
|---|---|---|---|---|---|
| Requisitos funcionais (RF) | 10 | 23 | 14 | 6 | 3 |
| Requisitos não funcionais (RNF) | 6 | 12 | 7 | 5 | 0 |
| Regras de negócio (RN) | 5 | 13 | 9 | 4 | 0 |
| **Total** | | **48** | **30** | **15** | **3** |

### 6.2 Cobertura das categorias de RNF

| Categoria | Requisitos |
|---|---|
| Desempenho | RNF01, RNF02, RNF03, RNF10 |
| Segurança | RNF04, RNF05, RNF09, RNF12 |
| Disponibilidade | RNF06 |
| Usabilidade e acessibilidade | RNF07, RNF11 |
| Compatibilidade | RNF08 |

Todas as 5 categorias previstas no enunciado estão cobertas (mínimo exigido: 4).

### 6.3 Conformidade com o enunciado

| Entregável | Exigência | Situação | Seção |
|---|---|---|---|
| Descrição do sistema | Parágrafo sobre o negócio e os tipos de usuário | Atendido | 2 |
| Requisitos funcionais | Mínimo de 10, no formato "O sistema deve permitir que [usuário] [ação]" | 23, todos no formato | 3 |
| Requisitos não funcionais | Mínimo de 6, mensuráveis, em ao menos 4 categorias | 12, todos com medida, 5 categorias | 4 e 6.2 |
| Regras de negócio | Mínimo de 5, válidas mesmo sem o sistema | 13 | 5 |
| Tabela de requisitos | Código, descrição e prioridade em cada requisito | Atendido (com usuário, categoria ou tema como apoio) | 3, 4 e 5 |
