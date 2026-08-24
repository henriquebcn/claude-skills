> **Precedência:** use este arquivo pelo **método** (estrutura de prompt, costuras,
> movimentos, linguagem de lente, workflows). Onde ele nomear modelo ou versão, ignore —
> slug, versão e limites vêm de `00-execucao-magnific.md`.

---

# Image Techniques

Fonte: The Prompting Handbook (Magnific, jul/2026 v1.2), Parte 01 — Prompting for Image.

## Estrutura de prompt de imagem

Como você escreve o prompt hoje importa mais que qualquer "quality tag" que você adicione: descreva uma cena coerente e o modelo segue. Os modelos de raciocínio (Nano Banana Pro e 2, GPT Image 2, e a linha Seedream) leem um prompt cheio de partes antes de renderizar, então aguentam bem quando a cena tem muitos sujeitos ou muito detalhe.

| Parte | O que responde | No prompt |
|---|---|---|
| Sujeito | Quem ou o que está no quadro | uma garrafa de colônia preto-fosco |
| Ação/estado | O que está fazendo, ou sua condição | uma gota atinge a ardósia numa respingo em coroa |
| Cenário | Onde, e sobre o quê | sobre ardósia molhada, fundo carvão |
| Luz | Nomeie o tipo de luz | luz rasante dura vinda da direita, sombras profundas |
| Composição | Onde as coisas ficam no quadro | terço direito do quadro, enquadramento macro apertado |
| Estilo | O acabamento | fotorrealista |

**Regras:**
- Cena, não tags. Diga o sujeito e o que ele está fazendo, onde, sob que luz, enquadrado como, em qual estilo. Pule boosters como "8K" ou "masterpiece".
- Cite o texto na imagem. Coloque as palavras exatas entre aspas para que renderizem corretamente; especifique o posicionamento ("título no topo-centro"). O mesmo vale para copy de produto: repita o rótulo ou texto da embalagem literalmente no prompt, ou o modelo vai inventar o seu próprio.
- Itere barato, entregue nítido. Explore em 1K, depois re-rode o resultado escolhido em 2K–4K.
- Trave a identidade com referências quando precisar do mesmo personagem ou produto ao longo de um conjunto.
- Produtos reais são o teste difícil. Detalhes, texturas e o tipo do rótulo têm que sobreviver ao render. Nano Banana 2 aguenta melhor para imagens (gerando e editando), e Seedance 2.5 para vídeo. Dê zoom no rótulo antes de entregar.

## Texto na imagem

Palavras são onde a maioria dos prompts desmorona, e onde usuários novos erram constantemente. O truque: os modelos posicionam texto como um designer posicionaria, não como um redator digitaria — dê o briefing do layout, cite as palavras.

**O que funciona:**
- Coloque cada palavra entre aspas, exatamente como deve ser lida, e diga onde ela vai ("headline atravessando o topo").
- Dê o briefing de zonas, colunas e hierarquia como um designer faria. Mantenha a poucos elementos de texto, em um ou dois tamanhos.
- Quando uma palavra continua saindo errada, soletre-a letra por letra no prompt, ex.: "o rótulo diz STUDIO: S, T, U, D, I, O."
- Seedream e GPT Image 2 são os mais fortes para texto; Recraft segura o texto mais longo de forma confiável.

**O que falha, e por quê:**
- Texto sem aspas vira paráfrase: o modelo trata como um tema, não como um roteiro.
- Parágrafos longos e muitos rótulos pequenos degradam em formas, porque o texto é desenhado, não tipografado.
- Não espere uma fonte ou kerning exatos; conserte uma palavra teimosa numa passagem de edição em vez de re-rodar o design inteiro.

## Edição de imagem

A edição agora é conversacional: você digita a mudança em vez de mascarar à mão, e cada modelo agrega sua própria especialidade.

**Regra de ouro:** diga o que mudar e o que manter numa única frase, ex. "substitua o fundo, mantenha o sujeito exatamente." Nomeie só o que deve se mover.

- **Editar uma região, ou relightar a cena** — Nano Banana 2 é o editor do dia a dia: seleciona e refina qualquer região, muda ângulo de câmera, foco ou grade de cor, e reilumina uma cena de dia para noite. Recorra ao Pro só quando a edição precisa de refinamento maior.
- **Combinar várias referências numa** — Seedream mescla até dez referências preservando rostos, luz e tom; Nano Banana Pro mantém até cinco personagens e catorze objetos coerentes.
- **Vetores verdadeiros e arte on-brand** — Recraft produz vetores verdadeiramente editáveis (SVG), não só PNG, e reforça um estilo de marca treinado. Magnific também consegue traçar qualquer imagem raster para SVG, além de fazer upscale, in/outpaint, e remover fundos.
- **Fazer instruções acertarem exatamente** — Coloque o texto exato entre aspas para edições de texto, e nomeie só o que deve mudar para o resto do quadro ficar parado. Fraco: "conserte o headline." Forte: "Mude o texto do headline apenas, para 'FOCUS'. Mantenha tipografia, tamanho, cor e posição."
- Rotule referências diretamente como @image1, @image2, etc., e dirija-se a elas no prompt.

## Field notes: matando o "slop"

Deixado sozinho, todo modelo deriva para o mesmo padrão: sujeito centralizado e olhando para a lente, posado e uniformemente iluminado, tudo em foco, com um brilho processado por cima. Existe uma palavra pra isso agora, e a sua audiência a conhece: slop. As pessoas percebem em meio segundo, e isso diz a elas que uma marca não se importou o suficiente para olhar. Nunca entregue isso.

Slop é o padrão, então cada parâmetro que você define (o enquadramento, o momento, a lente, a hora do dia, a luz) move a imagem um passo para longe dele; cada escolha que você deixa em aberto, o modelo preenche com sua resposta mais mediana.

O conserto é dois hábitos:
1. **Dirigir o plano** (enquadramento fora do centro, um momento real, profundidade) — isso é seu para nomear.
2. **Finalizar a grade** rumo a um vidro cinematográfico suave: contraste gentil, roll-off de foco cremoso, grão fino uniforme.

**THE FILM-LOOK LINE** (imagem + vídeo):
```
soft cinematic lens, shallow depth of field with creamy focus roll-off, gentle contrast with soft highlight roll-off, fine uniform film grain, no oversharpening, no digital look
```

**THE SKIN-REALISM BLOCK** (sempre que há pele visível):
```
Natural skin texture: realistic pores, fine hairs, subtle veining, a faint highlight. Tactile and real, not retouched plastic.
```

**Banned words** — essas palavras convocam o slop, nunca as escreva: *ultra sharp · hyper detailed · crisp · razor sharp · 8K clarity · HDR · ultra-realistic detail*. Grão é o único artefato de filme que vale a pena manter; nunca poeira, arranhões, ou "old damaged film".

### Exemplo: não dirigido → dirigido (mesmo modelo, mesmo sujeito)

**Não dirigido:** "A smiling woman holding a basket of vegetables at a farmers market stall." — limpo e competente, mas não dirigido: sujeito centralizado, de frente para a lente, sorriso posado, tudo em foco. Instantaneamente reconhecível como AI stock.

**Dirigido:**
```
Re-compose the reference as a directed documentary photograph. She is off-centre on the right third, turned three-quarters away, caught mid-movement arranging produce and laughing at someone off-frame. Blurred crate and vegetables in the near foreground on the left; shallow depth of field, the market melts into bokeh. Late-afternoon side light from the left, warm, soft rim light on her hat. Natural matte skin with visible pores and flyaway hairs. 35mm reportage film look, muted palette, faded blacks, gentle contrast, fine grain, no HDR.
```

Conte as escolhas: cada uma é um passo para longe do padrão.

## Field notes: controlando o quadro

O modelo preenche cada espaço que você deixa aberto. Estes quatro hábitos fecham os espaços que mais tiram um quadro do briefing.

- **Vazamento de palavra (word leakage):** uma palavra de humor colore o quadro inteiro, não só a coisa que ela descreve. Escreva "dewy" ou "sensual" em qualquer lugar, mesmo sobre a iluminação, e o modelo empurra a imagem inteira para sugestivo: roupas começam a escorregar e expressões ficam de bico. Contra-ataque com instruções explícitas, mesmo quando parecem desnecessárias. Ex.: "alças ficam arrumadas no lugar; lábios fechados e relaxados."
- **Negative prompts:** mantenha uma lista padrão de banimento e cole em todo prompt de retrato: *smiling, glamour makeup, jewelry, plastic smooth skin, dramatic rim light, colored background, soft focus*. Escale só quando necessário: *no pouting, no parted lips*.
- **Soletre palavras teimosas:** quando o texto renderizado continua embaralhando uma palavra ("FOIUS" em vez de FOCUS), reafirme letra por letra no prompt de edição: "spelled F, O, C, U, S".
- **Character sheets:** para personagens recorrentes, veja a seção abaixo.

## Character sheets

Para personagens recorrentes, nada compensa mais: construa uma character sheet de três painéis antes de um personagem aparecer duas vezes em qualquer lugar, e faça dela a referência mestra. Toda geração posterior leva a sheet como referência; todo prompt descrevendo o personagem é escrito a partir dela. Quando a identidade já existe, comece a partir de um retrato de referência; quando não existe, gere a sheet a partir de texto.

### Template de prompt (a partir de uma referência)
```
reference: [portrait] · Character sheet: one 16:9 frame divided into three equal panels on a pure white studio background. Left panel: straight-on head-and-shoulders portrait. Centre panel: exact side profile portrait. Right panel: full body, standing relaxed. The same [pessoa] in all three panels, the [pessoa] from the reference image, keeping her/his identity exactly: [características e figurino detalhados]. Soft even studio light, no props, no text, fine film grain, photorealistic.
```

**Regra:** quando o personagem muda (novo figurino, novo corte de cabelo, nova idade), a sheet muda primeiro. Regenere-a uma vez com a mudança descrita, e continue prompting a partir da nova sheet; um personagem tem exatamente uma sheet vigente a qualquer momento.

## Field notes: palavras que funcionam (vocabulário de imagem)

Metade do prompting é saber o nome do look. Empilhe duas ou três palavras por prompt, nunca todas: palavras de look empilhadas se diluem entre si, e a mais forte para de funcionar.

- **Luz:** *shadowplay* é a palavra-chave de iluminação mais confiável nos testes — luz natural e sofisticada com estrutura de sombra real. Combina bem com *cinematic*. Outras: single soft key from upper left · hard shaft of light · practical light only · low-key · rim light · golden hour.
- **Grade & mood** (máx. 2-3, além disso se cancelam): muted palette · faded blacks · gentle contrast · cinematic · editorial · quiet-luxury · understated.
- **Textura:** fine uniform film grain · visible pores · tactile fabric weave · atmospheric haze · soft highlight bloom.
- **Composição:** generous negative space · centered, deadpan framing · chest-up crop · slight three-quarter angle · leading lines.
- **Blur & foco** (diga o efeito, não o equipamento): background melts into soft blur · creamy focus roll-off · subject razor sharp against a soft distance · only the label in focus.
- **Combinações testadas:** shadowplay + cinematic + fine film grain (luz natural sofisticada) · muted palette + faded blacks + negative space (produto quiet-luxury) · practical light only + atmospheric haze (interiores habitados).
- **Números de equipamento são alavancas fracas.** Em testes da equipe através de quase todos os modelos, distâncias focais e aberturas (35mm, 50mm, f/1.2) quase não registram: os modelos ainda não diferenciam essas configurações técnicas (GPT Image 2 é a exceção parcial). Mantenha números de equipamento se quiser, mas sempre pareie com o efeito visível desejado, porque a linguagem do efeito é o que o render realmente responde.
