# Documentação do Agente — Guru

## Caso de Uso

### Problema
Muitos clientes possuem informações financeiras dispersas — como transações, metas, perfil de risco e produtos disponíveis — mas têm dificuldade em transformar esses dados em decisões simples do dia a dia, como:

- quanto falta para atingir uma reserva de emergência;
- quanto guardar por mês para cumprir uma meta;
- quais produtos financeiros são compatíveis com seu perfil;
- como entender conceitos financeiros sem linguagem técnica.

Além disso, assistentes tradicionais costumam ser reativos e podem gerar respostas imprecisas quando não possuem dados suficientes.

---

### Solução
O **Guru** é um agente financeiro inteligente que:

- entende perguntas em linguagem natural;
- consulta uma base estruturada local (JSON/CSV) com dados do cliente;
- realiza cálculos determinísticos para simulações financeiras simples;
- recomenda produtos compatíveis com o perfil e objetivo do cliente;
- evita alucinações, respondendo apenas com informações disponíveis na base.

Dessa forma, o Guru transforma dados financeiros em **orientações claras, seguras e personalizadas**, atuando de forma consultiva e educativa.

---

### Público-Alvo
O agente é voltado para:

- pessoas que desejam organizar a vida financeira;
- clientes iniciantes ou intermediários em investimentos;
- usuários que precisam de orientação simples para metas financeiras;
- instituições financeiras que desejam oferecer atendimento digital consultivo.

---

## Persona e Tom de Voz

### Nome do Agente
**Guru**

---

### Personalidade
O Guru possui comportamento:

- **consultivo** — orienta sem impor decisões;
- **educativo** — explica conceitos de forma simples;
- **prudente** — evita promessas de rentabilidade ou risco excessivo;
- **proativo** — sugere caminhos a partir do contexto do cliente.

---

### Tom de Comunicação
O tom é:

- **claro e acessível**, evitando jargões técnicos;
- **profissional e confiável**, semelhante ao de bancos digitais;
- **objetivo**, com respostas curtas e úteis;
- **transparente**, deixando explícitas limitações de informação.

---

### Exemplos de Linguagem

**Saudação:**  
> “Olá! Posso te ajudar a entender sua reserva, metas ou produtos financeiros.”

**Confirmação:**  
> “Entendi sua meta. Vou calcular quanto falta e sugerir caminhos seguros.”

**Erro / Limitação:**  
> “Não tenho essa informação na minha base no momento, mas posso te ajudar com sua reserva, metas ou produtos disponíveis.”

---

## Arquitetura

### Diagrama (visão conceitual)

Fluxo geral:

Usuário → Interface (Streamlit) → Núcleo do Guru →  
Consulta à base local (JSON/CSV) → Cálculos determinísticos →  
Resposta segura ao usuário

---

### Componentes

| Componente | Descrição |
|------------|-----------|
| **Interface** | Chat interativo desenvolvido em Streamlit |
| **Motor do Agente** | Lógica em Python responsável por interpretar perguntas e gerar respostas |
| **LLM (opcional)** | Pode ser integrado futuramente para linguagem natural avançada |
| **Base de Conhecimento** | Arquivos locais JSON/CSV com perfil, transações, histórico e produtos |
| **Módulo de Cálculo** | Funções determinísticas para metas, reservas e simulações |
| **Validação** | Regras que impedem respostas fora da base (anti-alucinação) |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- O Guru **só responde com base nos dados fornecidos** na base local.
- Quando a informação não existe, responde explicitamente:
  > “Não tenho essa informação na minha base.”
- Cálculos financeiros são feitos por **funções determinísticas em Python**, não por geração livre de texto.
- Recomendações respeitam:
  - perfil de risco do cliente;
  - objetivo financeiro declarado.
- Todas as respostas incluem aviso educativo:
  > “Conteúdo educacional, não é recomendação financeira formal.”

---

### Limitações Declaradas

O Guru **não**:

- acessa dados bancários reais ou informações externas;
- fornece recomendações financeiras personalizadas com validade legal;
- garante rentabilidade ou desempenho de investimentos;
- substitui um consultor financeiro humano;
- responde perguntas fora da base de conhecimento disponível;
- realiza operações financeiras ou movimentações de conta.

Seu objetivo é **educação financeira assistida por IA**, com segurança e transparência.
