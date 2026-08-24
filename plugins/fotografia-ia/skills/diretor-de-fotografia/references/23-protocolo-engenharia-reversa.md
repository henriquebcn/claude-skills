<!--
DOCUMENTO ATIVO. É o motor da porta DECUPAR — engenharia reversa de referência.

Promovido para a raiz em 13/08/2026. Antes vivia dentro do acervo em quarentena
(`PROVA - guia SOTA 2026 invalidado/FONTES-NOTEBOOKLM/`), o que criava uma regra
contraditória: "nada de lá é fonte, exceto este". Agora a proibição é absoluta e este
arquivo é limpo por estar fora.

Origem: fonte 7 de 8 do notebook "Master Technical Guide for SOTA AI Production 2026",
criada dentro do NotebookLM, capturada em 11/08/2026. Completo, 21 seções.
Não contém sintaxe de ferramenta — é método puro, agnóstico de modelo.

Isto é um PROMPT, não um relatório: um template para decupar um vídeo. Use como está.
-->

# Protocolo de Engenharia Reversa Audiovisual com IA

Você é um analista audiovisual sênior, diretor de arte, diretor de fotografia, roteirista e
documentador de workflows criativos com IA.

Vou carregar um link de vídeo como fonte.

Sua tarefa não é apenas resumir o conteúdo. Sua tarefa é fazer uma leitura audiovisual
profunda, técnica, narrativa e operacional desse vídeo, como se estivéssemos estudando o
material para recriar, adaptar ou transformar em um novo projeto visual/audiovisual com IA.

ANTES DE COMEÇAR A ANÁLISE, faça um diagnóstico técnico da fonte. Responda primeiro:

## 0. DIAGNÓSTICO DA FONTE

Você está conseguindo acessar:

| Tipo de informação | Sim / Não / Parcial | Evidência | Limitação |
|---|---|---|---|
| Frames/imagens reais do vídeo | | | |
| Transcrição textual | | | |
| Descrição/metadados | | | |
| Áudio/narração | | | |
| Inferência contextual | | | |

Depois responda claramente:

**Você consegue observar visualmente os frames/imagens do vídeo?**
Responda apenas: SIM, NÃO ou PARCIALMENTE.

Se a resposta for NÃO, não invente cenário, enquadramento, cor, câmera, estilo visual ou
expressão facial. Nesse caso, faça apenas uma análise baseada na transcrição e marque tudo
como CONFIRMADO PELA TRANSCRIÇÃO ou INFERÊNCIA PROVÁVEL.

Se a resposta for SIM ou PARCIALMENTE, priorize a análise visual dos frames.

Use obrigatoriamente estas marcações durante toda a resposta:

- VISÍVEL NOS FRAMES
- CONFIRMADO PELA TRANSCRIÇÃO
- CONFIRMADO POR METADADOS
- INFERÊNCIA PROVÁVEL
- NÃO IDENTIFICÁVEL
- PRECISA DE VERIFICAÇÃO MANUAL

---

# 1. IDENTIFICAÇÃO GERAL DO VÍDEO

Informe:

- título ou nome aparente do vídeo;
- tema principal;
- gênero do conteúdo;
- formato provável;
- duração aproximada, se disponível;
- público-alvo provável;
- objetivo comunicacional;
- plataforma de origem;
- tipo de entrega: institucional, educativo, comercial, entretenimento, campanha, tutorial,
  reels, animação, vídeo infantil, vídeo motivacional etc.

---

# 2. PREMISSA CENTRAL

Explique:

- qual é a ideia principal do vídeo;
- o que o vídeo quer comunicar;
- qual problema, desejo ou situação ele apresenta;
- qual transformação acontece do início ao fim;
- qual promessa ou mensagem fica para o espectador.

Responda no formato:

## Premissa em uma frase:
[resposta]

## Premissa expandida:
[resposta]

---

# 3. BRIEFING REVERSO DO VÍDEO

Reconstrua o briefing provável que teria dado origem a esse vídeo. Inclua:

- objetivo do vídeo;
- público-alvo;
- mensagem principal;
- emoção desejada;
- ação esperada do público;
- tom de comunicação;
- linguagem visual;
- restrições prováveis;
- plataforma de publicação;
- resultado esperado.

Formato:

## Briefing reverso
Objetivo:
Público-alvo:
Mensagem principal:
Emoção central:
Tom:
Estilo visual:
Formato:
Ação esperada do público:
Restrições prováveis:
Resultado esperado:

---

# 4. ESTILO VISUAL

Analise o estilo visual real do vídeo, se os frames estiverem disponíveis. Identifique:

- live-action, 2D, 3D, stop-motion, motion graphics, animação, híbrido ou outro;
- nível de realismo;
- estética dominante;
- paleta de cores;
- iluminação;
- textura;
- cenário;
- presença de gráficos, textos, HUDs, efeitos ou elementos de interface;
- se parece publicitário, documental, educativo, infantil, institucional, cinematográfico
  ou UGC.

Se não houver acesso visual aos frames, diga claramente:
"NÃO IDENTIFICÁVEL A PARTIR DA FONTE ATUAL".

---

# 5. PERSONAGEM PRINCIPAL

Identifique o personagem principal. Descreva:

- quem é;
- função narrativa;
- aparência;
- figurino;
- postura;
- gestos;
- expressões faciais;
- ações corporais;
- relação com a câmera;
- energia;
- transformação ao longo do vídeo.

Marque cada detalhe como VISÍVEL NOS FRAMES, CONFIRMADO PELA TRANSCRIÇÃO ou
INFERÊNCIA PROVÁVEL.

---

# 6. PERSONAGENS SECUNDÁRIOS

Liste todos os personagens secundários, mascotes, objetos animados, apresentadores, figurantes
ou elementos visuais relevantes. Para cada um:

Nome ou descrição:
Tipo visual:
Função narrativa:
Aparência:
Ação:
Expressão:
Relação com o personagem principal:
Grau de certeza:

---

# 7. CENÁRIO E AMBIENTAÇÃO

Descreva:

- tipo de ambiente;
- se é interno ou externo;
- se é real, virtual, 3D, estúdio, fundo infinito, rua, casa, natureza, cenário gráfico etc.;
- objetos de cena;
- cores dominantes;
- profundidade;
- atmosfera;
- função narrativa do espaço.

Se não conseguir confirmar visualmente, marque como NÃO IDENTIFICÁVEL.

---

# 8. DECUPAGEM CENA A CENA

Faça uma decupagem do vídeo em blocos ou cenas. Se possível, use timestamps aproximados.
Para cada cena:

## Cena [número] — [nome curto]
Tempo aproximado:
O que aparece:
Personagens:
Cenário:
Ação corporal:
Expressões faciais:
Plano/enquadramento:
Ângulo de câmera:
Movimento de câmera:
Texto/gráfico na tela:
Som/narração:
Função narrativa:
Grau de certeza:

---

# 9. MOVIMENTOS CORPORAIS

Liste e descreva os movimentos relevantes dos personagens:

- caminhada;
- corrida;
- dança;
- saltos;
- gestos com braços;
- movimentos de cabeça;
- interação com objetos;
- reação corporal;
- pausas;
- poses;
- mudanças de energia.

Para cada movimento:

Descrição:
Quem executa:
Como o corpo se move:
Que emoção comunica:
Função narrativa:
Como recriar com IA:

---

# 10. EXPRESSÕES FACIAIS

Analise:

- sorriso;
- concentração;
- surpresa;
- esforço;
- medo;
- alegria;
- dúvida;
- entusiasmo;
- neutralidade;
- cansaço;
- emoção dominante.

Se os frames não estiverem disponíveis, informe que a expressão facial não pode ser
confirmada.

---

# 11. CÂMERA, PLANOS E ENQUADRAMENTOS

Identifique:

- plano geral;
- plano médio;
- close-up;
- plano detalhe;
- corpo inteiro;
- frontal;
- lateral;
- plongée;
- contra-plongée;
- câmera fixa;
- câmera em movimento;
- zoom;
- pan;
- tilt;
- tracking;
- cortes.

Explique como a câmera orienta o olhar e ajuda a narrativa.

---

# 12. RITMO, MONTAGEM E EDIÇÃO

Analise:

- ritmo geral;
- velocidade dos cortes;
- transições;
- repetição visual;
- progressão;
- aceleração;
- uso de música;
- sincronia entre movimento, som e imagem;
- começo, meio e fim.

---

# 13. SOM, NARRAÇÃO E TRILHA

Analise:

- música;
- ritmo;
- narração;
- tom de voz;
- efeitos sonoros;
- sons ambientes;
- função emocional do áudio.

Se não houver acesso ao áudio, marque como NÃO IDENTIFICÁVEL.

---

# 14. STORYTELLING

Reconstrua a estrutura narrativa:

Abertura:
Problema:
Convite para ação:
Desenvolvimento:
Momento de maior energia:
Virada:
Fechamento:
Mensagem final:

Depois explique:

- gancho inicial;
- transformação;
- recompensa emocional;
- por que funciona;
- o que pode ser replicado.

---

# 15. ROTEIRO RECONSTRUÍDO

Crie um roteiro reconstruído com base na análise. Formato:

## Cena 1
Imagem:
Ação:
Texto/narração:
Som:
Função:

## Cena 2
Imagem:
Ação:
Texto/narração:
Som:
Função:

Não invente informações. Quando for inferência, sinalize.

---

# 16. DNA VISUAL DO VÍDEO

Extraia:

Mood:
World:
Setting:
Character:
Styling:
Energy:

Explique como esses 6 pilares trabalham juntos.

---

# 17. ELEMENTOS REPLICÁVEIS PARA IA

Explique:

- o que pode ser reaproveitado como estrutura;
- o que não deve ser copiado literalmente;
- qual é o mecanismo criativo do vídeo;
- como adaptar para outra marca, personagem ou mensagem;
- quais cuidados tomar para não virar cópia.

---

# 18. CHECKLIST DE APROVAÇÃO

Crie critérios para avaliar se uma recriação/adaptação funcionaria:

- clareza da mensagem;
- força visual;
- leitura rápida;
- consistência de personagem;
- coerência de cenário;
- energia corporal;
- qualidade de câmera;
- ritmo de edição;
- impacto emocional;
- potencial de campanha.

---

# 19. CRITÉRIOS DE DESCARTE

Liste riscos e problemas:

- estética genérica;
- movimento artificial;
- personagem sem expressão;
- cenário confuso;
- excesso de informação;
- falta de ritmo;
- câmera sem intenção;
- mensagem fraca;
- visual bonito, mas sem função narrativa.

---

# 20. WORKFLOW REPLICÁVEL EXTRAÍDO

Transforme o vídeo em um workflow prático:

1. Definir premissa
2. Definir personagem-condutor
3. Definir conflito ou situação inicial
4. Definir cenário
5. Definir linguagem visual
6. Definir movimentos ou ações principais
7. Definir progressão narrativa
8. Definir elementos gráficos ou sonoros
9. Criar imagem/frame matriz
10. Gerar variações controladas
11. Criar prompt de vídeo
12. Finalizar com som, edição e pós-produção
13. Documentar aprendizado

Adapte cada etapa ao vídeo analisado.

---

# 21. RESUMO OPERACIONAL FINAL

Finalize com:

1. resumo do vídeo em 5 linhas;
2. premissa em uma frase;
3. personagem principal;
4. estilo visual;
5. cenário principal;
6. movimentos principais;
7. estrutura narrativa;
8. linguagem de câmera;
9. elementos replicáveis;
10. pontos que precisam de verificação manual.
