# Construindo seu Próprio Agente de IA com LLMs e RAG

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Wyllgner/oficina-agente-ia-rag/blob/main/oficina_agente_ia.ipynb)

Material da oficina prática apresentada em 03/11/2026, no Laboratório 1, na Trilha de Tecnologia.

**Palestrantes:** Wyllgner Amorim, Nicolas Sales e Gabriel Sérgio

Nesta oficina você constrói, passo a passo, um agente de IA que:

1. conversa usando um **LLM** (o Gemini);
2. consulta **seus próprios documentos** com **RAG** (*Retrieval-Augmented Generation*);
3. **decide sozinho** quando buscar no documento e quando usar ferramentas, como uma calculadora de datas.

No final, cada participante personaliza o agente para uma finalidade própria, definindo o comportamento, o objetivo, as ferramentas e a base de conhecimento.

## Conteúdo do repositório

| Arquivo | O que é |
| --- | --- |
| `oficina_agente_ia.ipynb` | Notebook da oficina, com TODOs, experimentos, checkpoints e gabarito |
| `documentos/` | Documentos de exemplo para usar como base de conhecimento do agente |
| `documentos/LEIA-ME.md` | Prompts sugeridos e perguntas de teste para cada documento |

## Como usar

1. Clique no botão **Abrir no Colab** no topo desta página e depois vá em **Arquivo > Salvar uma cópia no Drive**, para poder editar e guardar o seu progresso.
2. Crie uma chave gratuita da API do Gemini em [aistudio.google.com/apikey](https://aistudio.google.com/apikey).
3. No Colab, abra o ícone de **chave (Secrets)** na barra lateral, crie um secret chamado `GEMINI_API_KEY` com a sua chave e ative o acesso do notebook.
4. Rode as células de cima para baixo com `Shift + Enter`.

> Nunca cole sua chave diretamente no código nem compartilhe o notebook com ela.

## Roteiro da oficina

| Parte | Tema |
| --- | --- |
| 0 | Preparação: chave da API, instalação e conexão |
| 1 | Primeiro contato com o LLM e prompt de sistema |
| 2 | RAG: trechos, embeddings, busca por similaridade e resposta com contexto |
| 3 | De chatbot a agente: ferramentas, decisões do modelo e o loop do agente |
| 4 | Sua ferramenta própria, escolhida de um cardápio com três níveis |
| 5 | Os três testes mínimos e uma interface de chat com Gradio |
| 6 | Limitações e próximos passos |

## Documentos de exemplo

Para usar outro documento como base de conhecimento, vá até a célula 2.2 do notebook, troque `USAR_MEU_DOCUMENTO` para `True` e envie um arquivo `.txt` ou `.md`. Depois rode a célula 2.3 para indexar o documento.

| Documento | Assunto | Ferramentas que combinam |
| --- | --- | --- |
| `edital_bolsas_ic.md` | Edital de bolsas de Iniciação Científica | `dias_ate`, `dias_uteis_ate` |
| `receitas.md` | Caderno de receitas | `ajustar_porcoes` |
| `guia_plantas.md` | Cuidados com plantas de casa | `sortear_trechos_quiz` |

Todos os documentos são fictícios e foram criados apenas para fins didáticos.

## Tecnologias

- [Google Gemini API](https://ai.google.dev/) com a biblioteca `google-genai`
- [NumPy](https://numpy.org/) para a busca por similaridade
- [Gradio](https://www.gradio.app/) para a interface de chat
- [BrasilAPI](https://brasilapi.com.br/) e [ViaCEP](https://viacep.com.br/) nas ferramentas de desafio

## Privacidade

Tudo o que você envia ao agente vai para a API do Google. Não use documentos sensíveis, internos ou com dados pessoais, e confira os termos de uso do plano gratuito.
