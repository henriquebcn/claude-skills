> **Precedência:** os blocos injetáveis deste arquivo (film-look line, skin-realism block,
> banned words, negative prompts) são válidos e devem ser usados. As **duas linhas de
> roteamento de modelo** que aparecem aqui estão superadas — slug e versão vêm de
> `00-execucao-magnific.md`. Ver `34-magnific-catalogo-QUARENTENA.md`.

---

# Cheat Sheet

Tudo que é injetável, num só lugar. Fonte: The Prompting Handbook (Magnific, jul/2026 v1.2), Apêndice.

### The film-look line (imagem + vídeo)
Mata o padrão processado de IA em todo prompt: vidro suave, contraste gentil, grão fino uniforme.
```
soft cinematic lens, shallow depth of field with creamy focus roll-off, gentle contrast with soft highlight roll-off, fine uniform film grain, no oversharpening, no digital look
```

### Standard negative set (imagem)
Rode os negatives padrão para retirar a deriva usual; escale só quando um render se comportar mal.
```
smiling, glamour makeup, jewelry, plastic smooth skin, dramatic rim light, colored background, soft focus
```
Escalar: `no pouting, no parted lips, no seductive expression`

### Model routing (imagem + vídeo)
**Imagem:** NB Pro (cinematográfico/hero) · NB2 (edições/produto/volume) · GPT Image 2 (layout) · Recraft (pôsteres/vetores).
**Vídeo:** Seedance 2.5 (padrão) · Kling 3.0 (clonagem/física/texto em produto) · Happy Horse (orçamento apertado).

Exemplo de roteamento: still hero de perfume → Nano Banana Pro · substituir o fundo → Nano Banana 2 · pôster de show com tipografia display → Recraft V4.1 · filme de produto de 8 segundos → Seedance 2.5.

### Sempre · imagem
- Cite texto na imagem e soletre palavras teimosas letra por letra.
- Trave identidade com referências.
- Nomeie só o que deve mudar numa edição.
- Trabalhe a partir do que renderizou, não do que foi planejado; reescreva para frente a partir disso.

Exemplo:
```
Change the headline to read "FOCUS", spelled F, O, C, U, S, top-centre, same typeface and size; keep everything else exactly unchanged.
```

### The skin-realism block (imagem + vídeo)
Sempre que pele estiver visível, especifique que é tátil e real; senão os modelos retocam para plástico.
```
Natural skin texture: realistic pores, fine hairs, subtle veining, a faint highlight. Tactile and real, not retouched plastic.
```

### Banned words (imagem + vídeo)
Essas palavras convocam o slop; nunca as escreva. Grão é o único artefato de filme que vale a pena manter; poeira, arranhões e "old damaged film", nunca.
```
ultra sharp · hyper detailed · crisp · razor sharp · 8K clarity · HDR · ultra-realistic detail
```

### Keywords que funcionam (imagem)
Quando o look não vem, o vocabulário geralmente é o que falta.
```
shadowplay + cinematic + fine uniform film grain   → luz natural sofisticada
muted palette + faded blacks + generous negative space   → produto quiet-luxury
background melts into soft blur   → o que aberturas de lente não conseguem fazer
```

### Sempre · vídeo
- Encadeie em clipes de 30 segundos ou menos.
- No máximo três personagens rastreados.
- Um portal por filme.
- Repita a descrição do produto literalmente em cada clipe.
- Reafirme posições e direções de frente depois de cada corte.

Exemplo:
```
Clip 2 continues the final frame of clip 1: she stands at the counter facing left, camera over her right shoulder; she lifts the flask and turns to the window.
```
