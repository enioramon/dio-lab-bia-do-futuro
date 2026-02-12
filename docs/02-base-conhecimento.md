# Base de Conhecimento — Guru

## Visão Geral

O **Guru** utiliza uma base de conhecimento local composta por arquivos estruturados em **CSV** e **JSON**, armazenados na pasta `data/`.

Esses dados permitem:

- personalização das respostas ao usuário;
- execução de **cálculos financeiros determinísticos**;
- coerência com o perfil, metas e produtos disponíveis;
- integração segura com **IA generativa**, evitando alucinações.

A arquitetura segue o princípio:

> **dados e cálculos são determinísticos;  
> a LLM apenas interpreta e comunica.**

---

## Dados Utilizados

| Arquivo | Formato | Utilização no Agente |
|---------|---------|----------------------|
| `historico_atendimento.csv` | CSV | Contextualização de interações anteriores e possibilidade de memória futura |
| `perfil_investidor.json` | JSON | Perfil de risco, renda, patrimônio, objetivos e metas financeiras |
| `produtos_financeiros.json` | JSON | Catálogo de produtos com risco, finalidade e características |
| `transacoes.csv` | CSV | Base para análises futuras de comportamento financeiro e gastos |

---

## Adaptações nos Dados

Os dados mockados fornecidos pelo desafio foram **preservados em sua essência**, com pequenas adequações técnicas:

- organização centralizada na pasta `data/`;
- padronização de nomes de campos para leitura consistente em Python;
- utilização das **metas financeiras** do perfil para cálculos determinísticos (ex.: reserva de emergência);
- definição explícita de **nível de risco** e **finalidade dos produtos**, permitindo filtragem automática conforme perfil do investidor.

Não foram incluídos **dados reais ou sensíveis**, mantendo o projeto dentro do escopo educacional e seguro.

---

## Estratégia de Integração

### Carregamento dos Dados

Os arquivos JSON e CSV são carregados:

1. na inicialização do aplicativo Streamlit;
2. antes da renderização da interface;
3. uma única vez por sessão do usuário.

Isso garante:

- consistência nas respostas;
- baixo custo computacional;
- simplicidade arquitetural adequada ao contexto educacional.

---

### Uso dos Dados pelo Agente

O Guru utiliza os dados de forma **determinística e auditável**:

#### Perfil do investidor
Usado para:

- personalizar respostas;
- validar compatibilidade de risco;
- identificar metas, prazos e objetivos financeiros;
- responder consultas diretas (renda, patrimônio, perfil).

#### Produtos financeiros
Utilizados para:

- explicar características de cada produto;
- sugerir opções compatíveis com risco e objetivo;
- impedir recomendações fora do catálogo local.

#### Transações e histórico
Atualmente disponíveis para:

- contextualização futura;
- expansão para análises de gastos e comportamento financeiro.

---

## Integração com IA Generativa

Diferentemente de chatbots tradicionais:

- os dados **não são inseridos diretamente em prompts livres**;
- o **Guru Core** consulta a base local e produz:
  - fatos;
  - cálculos;
  - listas de produtos válidos.

Somente depois disso a **LLM** é utilizada para:

- interpretar perguntas em linguagem natural;
- redigir respostas claras e profissionais.

Esse modelo reduz significativamente o risco de:

- alucinação de dados financeiros;
- inconsistência de números;
- recomendações fora do escopo.

---

## Exemplo de Contexto Interno

Exemplo simplificado de informações utilizadas pelo agente:

### Dados do cliente

- Nome: João Silva  
- Idade: 32 anos  
- Perfil de investidor: Moderado  
- Renda mensal: R$ 5.000  
- Reserva atual: R$ 10.000  

### Meta principal

- Completar reserva de emergência  
- Valor necessário: R$ 15.000  
- Prazo: 2026-06  

### Produtos compatíveis

- Tesouro Selic — baixo risco, indicado para reserva  
- CDB com liquidez diária — baixo risco, uso conservador  

Com base nesse contexto, o Guru pode:

- calcular o valor faltante para a meta;
- estimar o aporte mensal necessário;
- sugerir produtos adequados com segurança.

---

## Considerações de Segurança

A base de conhecimento segue princípios de **privacidade, auditabilidade e confiabilidade**:

- utiliza exclusivamente **dados fictícios (mock)**;
- não acessa sistemas bancários reais;
- não armazena informações sensíveis;
- permite rastreabilidade completa das respostas, pois todos os dados são locais.

Essa abordagem reforça o caráter:

> **educacional, seguro e transparente** do Guru.
