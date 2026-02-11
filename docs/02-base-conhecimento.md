# Base de Conhecimento — Guru

## Dados Utilizados

O Guru utiliza uma base de conhecimento local composta por arquivos estruturados em **CSV** e **JSON**, localizados na pasta `data/`.

Esses dados permitem personalizar respostas, realizar simulações financeiras e manter coerência com o perfil do cliente.

| Arquivo | Formato | Utilização no Agente |
|---------|---------|----------------------|
| `historico_atendimento.csv` | CSV | Recuperar contexto de interações anteriores e temas já discutidos |
| `perfil_investidor.json` | JSON | Identificar perfil de risco, objetivos, renda, patrimônio e metas financeiras |
| `produtos_financeiros.json` | JSON | Disponibilizar catálogo de produtos compatíveis com perfil e objetivo |
| `transacoes.csv` | CSV | Possibilitar análise de gastos e comportamento financeiro do cliente |

> [!TIP]
> Para evoluções futuras, o Guru pode integrar datasets financeiros públicos (ex.: Hugging Face), desde que compatíveis com o escopo educacional e com validação de segurança.

---

## Adaptações nos Dados

Os dados mockados fornecidos pelo desafio foram **mantidos em sua estrutura original**, com pequenas adequações voltadas à simulação do comportamento do agente:

- organização dos arquivos na pasta `data/` para carregamento centralizado;
- padronização de nomes de campos para facilitar leitura pelo código Python;
- utilização das metas financeiras do perfil do cliente para cálculos determinísticos (ex.: reserva de emergência);
- definição de produtos com **níveis de risco e finalidade**, permitindo filtragem automática conforme perfil do investidor.

Não houve inclusão de dados reais ou sensíveis, mantendo o projeto dentro do escopo educacional do desafio.

---

## Estratégia de Integração

### Como os dados são carregados?

Os arquivos **JSON** e **CSV** são carregados no início da execução do aplicativo Streamlit, utilizando funções auxiliares em Python.

Esse carregamento ocorre:

1. na inicialização da sessão do usuário;
2. antes da renderização da interface;
3. garantindo que todas as respostas utilizem a mesma base de contexto.

Essa abordagem permite:

- consistência nas respostas;
- baixo custo computacional;
- simplicidade de implementação para ambiente educacional.

---

### Como os dados são usados no agente?

O Guru utiliza os dados de forma **determinística e contextual**:

- **Perfil do investidor**  
  Usado para:
  - personalizar recomendações;
  - validar compatibilidade de risco;
  - identificar metas e prazos.

- **Produtos financeiros**  
  Utilizados para:
  - explicar características de cada produto;
  - sugerir opções alinhadas ao perfil e objetivo.

- **Transações e histórico de atendimento**  
  Atualmente disponíveis para:
  - contextualização futura;
  - expansão para análises de gastos e comportamento financeiro.

Os dados **não são inseridos diretamente em prompts generativos**.  
Em vez disso, são consultados por funções Python, evitando alucinações e garantindo precisão.

---

## Exemplo de Contexto Utilizado pelo Guru

A seguir, um exemplo simplificado de como as informações são organizadas internamente para responder ao usuário:

Dados do Cliente
- Nome: João Silva
- Idade: 32 anos
- Perfil de investidor: Moderado
- Renda mensal: R$ 5.000
- Reserva atual: R$ 10.000

Meta principal
- Completar reserva de emergência
- Valor necessário: R$ 15.000
- Prazo: 2026-06

Produtos compatíveis
- Tesouro Selic — baixo risco, indicado para reserva
- CDB com liquidez diária — baixo risco, uso conservador

Esse contexto permite que o Guru:

- calcule quanto falta para a meta;
- estime quanto guardar por mês;
- sugira produtos adequados com segurança.

---

## Considerações de Segurança

A base de conhecimento do Guru segue princípios de **privacidade e confiabilidade**:

- utiliza apenas **dados fictícios (mock)**;
- não acessa sistemas bancários reais;
- não armazena informações sensíveis;
- permite auditoria completa das respostas, pois todos os dados são locais.

Essa abordagem reforça o caráter **educacional, seguro e transparente** do agente.

