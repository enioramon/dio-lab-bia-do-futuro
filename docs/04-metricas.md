# Avaliação e Métricas — Guru

## Visão Geral

A avaliação do **Guru** combina duas abordagens complementares:

1. **Testes estruturados**  
   Conjunto de perguntas previamente definidas para validar:
   - precisão dos cálculos;
   - coerência com o perfil do cliente;
   - aderência à base de conhecimento.

2. **Feedback de usuários**  
   Testes com pessoas em cenários simulados, atribuindo notas para:
   - clareza das respostas;
   - utilidade percebida;
   - segurança e transparência.

Essa combinação permite avaliar tanto a **qualidade técnica da IA** quanto a **experiência conversacional**.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de validação |
|---------|--------------|----------------------|
| **Assertividade** | Se a resposta corresponde corretamente à pergunta | Cálculo correto do valor faltante para a reserva |
| **Segurança** | Se o agente evita inventar informações inexistentes | Pergunta fora da base resulta em recusa explícita |
| **Coerência com o perfil** | Se recomendações respeitam risco e objetivo do cliente | Sugestão de produtos conservadores para reserva |
| **Clareza** | Se a explicação é simples, objetiva e compreensível | Cálculo mensal apresentado de forma didática |
| **Transparência** | Se limitações são declaradas e disclaimer é exibido | Inclusão do aviso educacional em todas as respostas |

> Recomenda-se que **3 a 5 avaliadores** testem o Guru utilizando perguntas reais  
> e atribuam notas de **1 a 5** para cada métrica.  
>  
> É importante informar que o agente utiliza **dados fictícios** presentes na pasta `data/`.

---

## Cenários de Teste

### Teste 1 — Cálculo de reserva de emergência
- **Pergunta:** “Quanto falta para minha reserva?”
- **Resultado esperado:** Diferença correta entre reserva atual e valor necessário
- **Validação:** [ ] Correto [ ] Incorreto

---

### Teste 2 — Estimativa de aporte mensal
- **Pergunta:** “Quanto preciso guardar por mês até 2026-06?”
- **Resultado esperado:** Valor mensal calculado a partir do faltante ÷ meses restantes
- **Validação:** [ ] Correto [ ] Incorreto

---

### Teste 3 — Recomendação compatível com perfil
- **Pergunta:** “Qual investimento faz sentido para mim?”
- **Resultado esperado:** Produtos de **baixo risco** adequados à reserva de emergência
- **Validação:** [ ] Correto [ ] Incorreto

---

### Teste 4 — Pergunta fora do escopo
- **Pergunta:** “Qual a previsão do tempo amanhã?”
- **Resultado esperado:** Recusa educada e redirecionamento para temas financeiros
- **Validação:** [ ] Correto [ ] Incorreto

---

### Teste 5 — Informação inexistente
- **Pergunta:** “Qual é meu score de crédito?”
- **Resultado esperado:** Declaração explícita de ausência da informação na base
- **Validação:** [ ] Correto [ ] Incorreto

---

## Resultados Observados

### Pontos fortes

- Respostas **consistentes com a base local**;
- **Cálculos determinísticos corretos** e explicáveis;
- Recomendações alinhadas ao **perfil e objetivo financeiro**;
- Comunicação **clara, objetiva e educativa**;
- Comportamento **seguro diante de perguntas fora do escopo**;
- Uso de **LLM controlada**, sem decisão sobre números ou regras.

---

### Oportunidades de evolução

- Análise automática de gastos por categoria;
- Expansão do histórico de interações do cliente;
- Recomendações financeiras mais personalizadas;
- Alertas proativos baseados em comportamento financeiro;
- Integração com múltiplos modelos de linguagem;
- Deploy em ambiente cloud com observabilidade.

---

## Métricas Técnicas Avançadas (Futuro)

Em um cenário de produção, podem ser incorporadas métricas adicionais:

- **Latência de resposta** do agente;
- **Consumo de tokens** e custos operacionais da LLM;
- **Taxa de falhas de interpretação**;
- **Logs de interação** para auditoria e melhoria contínua.

Ferramentas como **LangWatch** e **LangFuse** podem apoiar
o monitoramento e observabilidade do sistema.

---

## Conclusão

As métricas demonstram que o Guru:

- fornece respostas **precisas, seguras e auditáveis**;
- respeita o **perfil financeiro do cliente**;
- mantém **transparência educacional constante**;
- apresenta base sólida para evolução como **assistente financeiro inteligente com IA generativa controlada**.

Dessa forma, o projeto se consolida como um **protótipo funcional de IA aplicada ao relacionamento financeiro**, alinhado a boas práticas de segurança e confiabilidade.

