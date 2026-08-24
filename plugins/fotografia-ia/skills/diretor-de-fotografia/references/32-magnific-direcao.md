> **Precedência:** use este arquivo pelo **método** (estrutura de prompt, costuras,
> movimentos, linguagem de lente, workflows). Onde ele nomear modelo ou versão, ignore —
> slug, versão e limites vêm de `00-execucao-magnific.md`.

---

# Directing the Shot

Fonte: The Prompting Handbook (Magnific, jul/2026 v1.2), Parte 03 — Directing the Shot.

Câmera, lente e performance: a linguagem que transforma uma descrição num plano dirigido.

## Regras de motor: encadeando clipes — as cinco costuras (seams)

Um filme de múltiplos clipes é uma corrente de costuras, e cada costura responde uma pergunta: o próximo clipe continua este frame, continua este movimento, atravessa algo, ou quebra limpo?

| Costura | O que é |
|---|---|
| **Frozen handoff** | O último frame do clipe N vira o primeiro frame do clipe N+1: termine num estado congelável e reafirme-o exatamente. |
| **Action bridge** | Um movimento começa no fim de um clipe e completa no início do próximo, de um ângulo novo. Nomeie o movimento e sua direção em ambos os prompts. |
| **Match cut** | Dois frames compartilham forma, posição ou cor enquanto a cena muda. Nomeie o elemento que rima em ambos os prompts. |
| **Portal** | A câmera empurra para dentro de algo que preenche o quadro (uma pupila, vapor, uma porta) e emerge em outro lugar. Racione-o: um por filme, ou soa como gimmick. |
| **Hard cut** | Uma quebra limpa; lógica de montagem. O padrão quando nada precisa se conectar. |

**Mapeamento briefing → costura:** "sem costura / um único take / deveria fluir" → frozen handoff · "corte para / enquanto isso / vinhetas" → hard cuts · "se transforma em / se torna" → match cut · quando o briefing é silencioso → hard cut é o padrão, nunca portal.

**Duas regras adicionais:**
- Trabalhe a partir do que realmente renderizou, não do que foi planejado: antes de escrever o próximo clipe, extraia o frame final real e reescreva a abertura a partir dele.
- Trave o produto: repita sua descrição palavra por palavra em cada prompt de clipe; essa repetição é o que mantém consistência através de gerações separadas.

Mantenha clipes encadeados em 30 segundos cada, no máximo.

## Regras de cena (a física de uma cena gerada)

Estas são a física de uma cena gerada: como os motores rastreiam pessoas, objetos e espaço dentro de um único plano. Escreva com elas e os clipes se seguram; escreva contra elas e as costuras aparecem.

- **Ação é intenção mais um movimento nomeado, nunca biomecânica.** Motores executam intenção; não conseguem seguir coreografia articulação-por-articulação. "Chute giratório de costas conecta," não "antebraço rotaciona 45° para desviar o gancho." Nomeie o que acontece e deixe o modelo encenar como acontece.
- **Emoções são física, não rótulos.** Um rótulo pede ao modelo para adivinhar um rosto; uma ação física diz exatamente o que renderizar. "Mandíbula se contrai, narinas se abrem," não "parece com raiva."
- **Só o que pode ser visto ou ouvido.** O prompt descreve uma filmagem de câmera, então cheiros, pensamentos e backstory renderizam como nada. Traduza-os em evidência visível: não "o ar cheira a cedro," mas "aparas de cedro na bancada, poeira flutuando na luz."
- **Sair do quadro significa sumir.** Qualquer coisa que sai do quadro está fora pelo resto daquele plano; nunca saia e reentre num único take contínuo. Fora de tela significa inexistente: mostre uma mudança de estado na câmera antes de referenciá-la.
- **Rastreie no máximo três personagens através dos cortes.** Além de três, as identidades começam a trocar: rostos migram entre corpos e detalhes de figurino trocam de lugar. Mantenha figurantes genéricos e sem nome; detalhe só os personagens que precisam permanecer reconhecíveis.
- **Componha em torno de espelhos, nunca para dentro deles.** Reflexos quebram a geografia da cena: o motor tem que inventar o quarto invertido, e geralmente inventa errado. Filme passando por um espelho ou mantenha-o num ângulo de relance; nunca deixe o reflexo carregar o plano.
- **Reestabeleça a cena depois de cada corte.** Reafirme posições e direções de frente, e mantenha a câmera de um lado da linha de ação (regra dos 180°) para que os personagens não troquem de lado do quadro.
- **Texto na tela livre é pouco confiável.** Declare uma zona segura de texto (ex.: "o terço direito do frame final cai em escuridão limpa") e aplique a tipografia na pós-produção. Para texto em rótulo de produto, Kling 3.0 segura melhor.

## Doze movimentos de câmera

| Movimento | O que faz |
|---|---|
| **Push-in** | Move em direção ao sujeito. Constrói tensão e intimidade; mantenha lento. |
| **Pull-back** | Recua para revelar. Isolamento, escala, finais: o plano de revelação. |
| **Pan** | Rotação horizontal, câmera fixa. O suspense mora no que você ainda não mostrou. |
| **Tilt** | O pan vertical. Tilt para cima num herói o faz ler como poderoso. |
| **Tracking** | Câmera viaja com o sujeito. Energia, movimento para frente, "você está lá." |
| **Arc / orbit** | Circula o sujeito. Um produto num pedestal limpo faz um giro completo; mantenha arcos em torno de pessoas abaixo de ~30°. |
| **Crane / jib** | Varre verticalmente num braço. Grandiosidade e escala: a visão de deus. |
| **Zoom** | Distância focal muda, câmera fica parada. Mais achatado que um dolly; zoom rápido = energia de videoclipe. |
| **Dolly zoom** | Câmera e lente se movem em direções opostas. O fundo se distorce, o sujeito se mantém — puro pavor. |
| **Whip pan / crash zoom** | Velocidade extrema para transições. Choque, comédia, para o scroll. |
| **Handheld** | Tremor natural, não estabilizado. Adicione "subtle" ou vira terremoto total. |
| **Static + ângulos** | Baixo, alto, Dutch, olho-de-pássaro, olho-de-minhoca. Baixo = poder; Dutch = inquietação; olho-de-pássaro = escala. |

**Regra de ouro:** um movimento por clipe, nunca empilhe. Adicione "slow" a quase tudo — movimentos lentos escondem o que o modelo não consegue renderizar de forma limpa; movimentos rápidos expõem cada falha.

## Linguagem de câmera e lente

Trate os termos abaixo como taquigrafia — sempre pareie com o efeito visível, já que os modelos mal diferenciam 35mm de 85mm, ou f/1.2 de f/8.

| Termo | No prompt | Efeito |
|---|---|---|
| Wide-angle · 14–24mm | "shot on a 24mm wide lens" | Expansivo, imersivo; leve distorção de borda |
| Standard · 35–50mm | "35mm" | Natural, próximo da visão humana |
| Telephoto · 85–135mm | "85mm portrait lens" | Compressão; favorecedor; fundo suave |
| Macro | "100mm macro" | Detalhe extremo; um sujeito minúsculo preenche o quadro |
| Anamórfico | "anamorphic, 2.39:1" | Widescreen; flares horizontais; bokeh oval |
| Abertura rápida | "f/1.8, shallow depth of field" | Isolamento de sujeito; bokeh cremoso |
| Foco profundo | "f/11, deep focus" | Nítido do primeiro plano ao fundo |
| Rack focus | "rack focus to her face" | Muda a atenção dentro de um único plano |

**Tamanhos de plano e ângulos:** estabelecedor/extreme wide (lugar e escala) · wide (sujeito completo em seu ambiente) · médio (da cintura para cima; o padrão conversacional) · close-up (rosto ou detalhe preenche o quadro) · extreme close-up (olhos, uma textura, um logo) · over-the-shoulder/POV (enquadrado atrás de um ombro, ou pelos olhos do personagem) · ângulo baixo/alto (poder para cima, vulnerabilidade para baixo) · Dutch angle (horizonte inclinado; inquietação e tensão) · bird's-eye/top-down (diretamente do alto; escala e padrão) · worm's-eye (do chão para cima; monumental).

## Diálogo

Modelos com áudio nativo (Seedance, Kling, Happy Horse) falam as falas que você escreve e sincronizam os lábios; Gemini Omni Flash também fala, mas não sincroniza com áudio fornecido por você. Coloque as palavras entre aspas e atribua-as a um personagem, mantenha cada fala no que cabe no clipe, e descreva a entrega. Um único orador por beat mantém a sincronia limpa; adicione "no subtitles" para evitar legendas queimadas.

**Exemplo:**
```
Close-up of a barista sliding a cup across the counter. She looks to camera and says, warmly, "Careful, it's hot." Soft café murmur, espresso hiss. No music. No subtitles.
```

## Timing beat-por-beat

Para um plano com mais de uma ação, coreografe com timecodes. Numere os beats a partir de 00:00, dê a cada um uma única ação, e mantenha o último beat dentro da duração do clipe. Isso impede o modelo de amontoar tudo no primeiro segundo, e permite sincronizar ação com a revelação de um produto ou um beat musical.

**Exemplo:**
```
6-second product shot, one continuous take. 00:00 the watch lies flat on black stone, still. 00:02 it rises and rotates slowly to face camera. 00:04 it settles as a rim light sweeps across the dial. SFX: low hum, soft click. No music. No subtitles.
```

## A audição: teste de tela da performance

A character sheet trava o rosto; a audição trava a performance. Antes de um personagem carregar uma cena real, rode um teste de tela: um self-tape curto que mostra como ele se move, fala e reage sob direção. Gere duas ou três tomadas com receitas de voz diferentes, escolha a performance vencedora, e anexe o clipe vencedor como referência de vídeo em toda cena que seguir — da mesma forma que a sheet acompanha para identidade. Decidir a atuação uma vez é muito mais barato do que re-rodar cenas até acertar por acidente.

**Receita:**
- Filme um self-tape, não um trailer: sala simples, medium close-up, altura dos olhos, foco raso. O quadro existe para revelar atuação, não espetáculo.
- Uma fala curta com subtexto: jogável de mais de uma forma, implicando alguém fora de câmera. Diálogo de cena, não lore ou narração.
- Uma receita de voz, no máximo três qualidades: ex. "exausta, terna, contida." Misture forças emocionais; um rótulo plano soa morto.
- Dirija a micro-atuação: um momento vocal (um começo quebrado, uma palavra estressada, uma rachadura silenciosa) e um pequeno comportamento físico (um desvio de olhar, tensão na mandíbula, um olhar para baixo e de volta).
- Termine sem resolução: deixe o silêncio se instalar antes e depois da fala. O momento suspenso é onde a performance mora.

**Exemplo:**
```
Cinematic self-tape audition, one continuous take. Medium close-up, locked-off eye-level camera, shallow depth of field: a woman in her 30s against a plain grey wall, soft window light from the left, listening to an off-camera reader. A beat of silence; she looks down, then back up. She says, quietly: "You knew. The whole time, you knew." Voice: controlled, hurt, almost warm; it catches on the second "knew." Jaw tightens, one slow blink, the trace of a smile that is not one. She holds eye contact and says nothing more. Natural skin texture, fine film grain, muted palette. No music. No subtitles.
```
