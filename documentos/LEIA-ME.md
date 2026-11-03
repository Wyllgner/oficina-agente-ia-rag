# Documentos de exemplo para a oficina

Para usar um destes documentos: na célula 2.2, troque `USAR_MEU_DOCUMENTO` para `True`, rode a célula, envie o arquivo e depois rode a 2.3 para indexar.

Todos foram testados com o `dividir_em_trechos` do notebook: nenhum trecho passa de cerca de 400 caracteres.

Datas calculadas com HOJE = 03/11/2026.

---

## edital_bolsas_ic.md · Edital de Iniciação Científica (12 trechos)

**Combina com:** `dias_ate`, `dias_uteis_ate`, `salvar_anotacao`, `sortear_trechos_quiz`

**Prompt sugerido:**
```
Você é o Assistente de Editais da FFTM.
Ajuda alunos a entender o Edital nº 07/2026 de bolsas de Iniciação Científica.
Hoje é {HOJE.isoformat()}.

Regras:
- Para qualquer dúvida sobre o edital, use a ferramenta buscar_documentos.
- Responda somente com base no que a busca retornar. Se não encontrar, diga que não encontrou.
- Para calcular quantos dias faltam para um prazo, use a ferramenta dias_ate.
- Responda em português, de forma curta, e cite a seção do edital.
```

**Perguntas de teste:**

| Pergunta | Resposta esperada |
| --- | --- |
| Quanto vale a bolsa? | R$ 700,00 por mês, durante 12 meses, com 20 h semanais |
| Quantos dias faltam para o fim das inscrições? | 24/11/2026, faltam 21 dias |
| Tenho CRA 6,8. Posso me inscrever? | Não, o mínimo é 7,0 |
| Quando sai o resultado final? | 15/12/2026, faltam 42 dias |
| Trabalho de carteira assinada. Posso ser bolsista? | Não, o bolsista não pode ter vínculo empregatício |
| Qual o valor da bolsa de mestrado? | Não está no documento |

`dias_uteis_ate("2026-11-24")` deve dar cerca de 14 dias úteis, porque 20/11 (Consciência Negra) é feriado nacional. O valor exato depende da lista de feriados da BrasilAPI.

---

## receitas.md · Caderno de receitas (14 trechos)

**Combina com:** `ajustar_porcoes`, `salvar_anotacao`

**Prompt sugerido:**
```
Você é o Chef Madeira, um assistente de cozinha simpático.
Ajuda as pessoas a preparar as receitas do Caderno de Receitas da Cozinha Madeira.

Regras:
- Para qualquer dúvida sobre receitas, ingredientes ou modo de preparo, use a ferramenta buscar_documentos.
- Só sugira receitas que estão no caderno. Se não encontrar, diga que a receita não está no caderno.
- Para mudar a quantidade de porções, use a ferramenta ajustar_porcoes para cada ingrediente.
- Responda em português, de forma curta e animada.
```

**Perguntas de teste:**

| Pergunta | Resposta esperada |
| --- | --- |
| Quanto tempo o pão de queijo fica no forno? | 25 a 30 minutos, a 200 °C |
| Quero fazer o suco de cupuaçu para 10 pessoas. Quanto de polpa? | 750 g (a receita rende 4 porções com 300 g) |
| Quero o bolo de cenoura para 6 pessoas. Quantos ovos? | 1,5 ovo (a receita rende 12 porções com 3 ovos) |
| Quanto tempo a carne seca fica de molho? | Pelo menos 12 horas, trocando a água 3 vezes |
| Como faço lasanha? | Não está no caderno |

Ponto bom para mostrar: no bolo de cenoura, o rendimento e os ingredientes ficaram em trechos diferentes. O agente pode precisar buscar mais de uma vez antes de chamar `ajustar_porcoes`.

---

## guia_plantas.md · Cuidados com plantas (9 trechos)

**Combina com:** `sortear_trechos_quiz`, `salvar_anotacao`, `dias_ate`

**Prompt sugerido:**
```
Você é a Flora, uma assistente de jardinagem.
Ajuda as pessoas a cuidar das plantas de casa com base no Guia Rápido de Cuidados com Plantas.
Hoje é {HOJE.isoformat()}.

Regras:
- Para qualquer dúvida sobre plantas, use a ferramenta buscar_documentos.
- Responda somente com base no guia. Se não encontrar, diga que o guia não fala sobre isso.
- Quando o usuário pedir um quiz, use a ferramenta sortear_trechos_quiz e crie uma pergunta por trecho.
- Responda em português, de forma curta e acolhedora.
```

**Perguntas de teste:**

| Pergunta | Resposta esperada |
| --- | --- |
| De quanto em quanto tempo rego a espada-de-são-jorge? | A cada 15 dias no verão e 30 no inverno, com o substrato seco |
| Tenho gato. Quais plantas do guia são perigosas? | Espada-de-são-jorge, jiboia e costela-de-adão |
| As folhas da minha jiboia estão amarelas. O que é? | Excesso de água |
| Tem bichinhos brancos na minha planta. O que faço? | Cochonilhas: limpar com álcool 70% e repetir após 7 dias |
| Me faz um quiz com 3 perguntas | Usa `sortear_trechos_quiz(3)` |
| Como cuidar de uma orquídea? | Não está no guia |

A pergunta do gato é boa para o Experimento 2: a resposta está espalhada em 3 trechos diferentes. Com `k=1`, o agente não encontra todas.
