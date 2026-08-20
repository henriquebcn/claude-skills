# Base de execução — stack SOTA no Magnific

## Finalidade

Camada de execução: qual modelo chamar, com que slug, que parâmetro existe de verdade e como
disparar via MCP. Não repete craft — decisão de câmera, luz e lente segue `AGENTS.md` e as
bases de cinematografia. Esta base responde "onde aperto o botão", não "o que filmar".

Leia quando a tarefa envolver gerar imagem ou vídeo no Magnific, ou quando for preciso
converter uma decupagem em chamada real.

Este catálogo reflete um plano específico num dado momento. **Revalide com
`video_models_list` e `images_models_list` antes de tratar qualquer número abaixo como atual:**
slugs mudam, limites mudam, e planos diferentes liberam modelos diferentes.

## Catálogo e escolha

**Vídeo**

| Modelo | slug | Use para |
| --- | --- | --- |
| Seedance 2.0 | `bytedance-seedance-pro-2.0` | padrão. 4–15 s, até 4K, 21:9, áudio nativo, lipsync, multishot, referências |
| Kling 3.0 | `kling-30` | 3–15 s, até 4K, multishot, referências `character`/`product`/`image` (exigem start frame), start/end frame, SFX |
| Kling 3.0 Omni | `kling-omni3` | como o 3.0, mais referência de **vídeo**; end frame exige start frame |
| Kling 3.0 Turbo | `kling-30-turbo` | 3–15 s, rápido, só start frame, sem referências |
| Kling 2.6 | `kling-26` | 5 ou 10 s, 1080p, SFX e controle de voz (até 2 vozes) |
| Kling 2.5 | `kling-25` | 5 ou 10 s, 720p/1080p, mudo, start/end frame, sem referências |
| Kling 3.0 / 2.6 Motion Control | `kling-motion-control-30` / `kling-motion-control` | transferência de performance; start frame é **vídeo** |
| Seedance 2.0 Mini | `bytedance-seedance-mini-2.0` | rascunho com áudio, 480p/720p |
| Seedance 2.0 Fast | `bytedance-seedance-fast-2.0` | rascunho rápido, 480p/720p |

**Imagem**

| Modelo | slug | Use para |
| --- | --- | --- |
| Seedream 5 Pro | `seedream-5-pro` | padrão. T2I, edição por referência, produto, personagem |
| Recraft V4.1 | `recraft-v4-1` | T2I puro, primeiro rascunho, exploração criativa |
| Nano Banana Pro | `imagen-nano-banana-2` | fidelidade máxima de marca no asset final |
| Nano Banana 2 Lite | `imagen-nano-banana-2-lite` | rascunho barato em volume (~11 s) |
| GPT 2 | `gpt-2` | texto legível, infográfico, diagrama, tipografia |

## Movimento de câmera — enum real do Seedance

Não descreva o movimento em prosa quando existir valor de enum. Use o valor; reserve a prosa
para intenção e peso.

- **Aproximação/afastamento:** `pushIn`, `pullOut`, `superDollyIn`, `superDollyOut`,
  `crashZoomIn`, `zoomIn`, `zoomOut`, `doubleDolly`
- **Translação:** `truckLeft`, `truckRight`, `moveLeft`, `moveRight`, `moveUp`, `moveDown`,
  `pedestalUp`, `pedestalDown`
- **Rotação no eixo:** `panLeft`, `panRight`, `tiltUp`, `tiltDown`, `whipPan`, `upwardTilt`,
  `downwardTilt`
- **Grua:** `jibUp`, `jibDown`, `craneUp`, `craneDown`, `craneOverTheHead`
- **Órbita:** `orbitLeft`, `orbitRight`, `360Orbit`, `leftCircling`, `rightCircling`
- **Acompanhamento:** `leftWalking`, `rightWalking`, `headTracking`, `snorricam`, `fpvDrone`
- **Ótica e defeito:** `fisheye`, `dutchAngle`, `focusChange`, `lensFlare`, `dirtyLens`,
  `lensCrack`, `lowShutter`, `handheld`
- **Ponto de vista:** `overhead`, `objectPov`, `scenicShot`, `stageLeft`, `stageRight`,
  `static`

Enquadramento e altura **não são** movimento: contra-plongée, plano detalhe e escala vão na
descrição, não no enum.

## Referências (Seedance 2.0)

Tipos: `image` (até 9), `video` (até 3), `character` (1), `product` (1), `style` (1), `color`,
`effect`, `audio` (até 3).

- Cada referência precisa de função explícita — ver hierarquia em
  `BASE-CINEMATOGRAFIA-PARA-IA-GENERATIVA.md`, seção 3.
- `image` e `video` são **proibidos junto com keyframes**. Escolha um caminho.
- Áudio vai em `references[]` com `type: audio`, nunca em `audioUrl`. mp3/wav, 2–15 s, exige
  uma referência visual junto; start frame não satisfaz esse requisito.
- Kling 2.5 **não aceita referências** — só start/end frame.

## Keyframes

- Seedance: `keyframes.start` e `keyframes.end`, proibidos com referência `image`/`video`.
- Kling 2.5 em **720p**: start frame **obrigatório**, end frame **proibido**.
- Kling 2.5 em 1080p: ambos liberados.
- Regra de craft inalterada: só use start/end entre estados geometricamente compatíveis.

## Multishot

Seedance 2.0 aceita até **6 planos numa geração**, de 1 a 12 s cada, com start frame por
plano. Use para cravar cadência de montagem na geração — cortes curtos abrindo para planos
longos — em vez de montar depois. Para identidade, produto ou mãos em precisão, continue
gerando planos separados.

## Fluxo MCP

1. `video_plan` primeiro — resolve e valida o slug.
2. `video_generate` com o slug verbatim.
3. `creations_show` para o usuário ver, depois `creations_wait` para confirmar e obter a URL
   final antes de encadear.
4. Imagem: `images_generate`. Arquivo local do usuário: `creations_upload_show` — nunca peça
   anexo no chat.
5. Nunca regere criação em fila.

## Como escrever o que o gerador obedece

Regras validadas em produção, comparando regerações lado a lado. Todas nascem do mesmo
princípio: **o gerador não simula, ele
renderiza. Descreva o resultado observável, nunca o mecanismo que o produziria.**

**1. Luz: descreva a aparência, não a origem.**
"Luz de janela a 45° pela esquerda" é uma causa — o modelo interpreta e erra o lado com
frequência. O que ele obedece é o que se vê no pixel:

> o lado do rosto voltado para a ESQUERDA é o lado aceso · a sombra do nariz cai para a
> DIREITA · as faces voltadas para a esquerda carregam o brilho · não há janela nem luz fria
> em nenhum ponto do lado direito do quadro

Trave também a **geometria da sala** com o mesmo bloco de texto em todos os planos da
sequência (onde está a janela, onde está o balcão). Sem isso o cenário espelha entre cortes.

**2. Identidade: amarre a um sinal binário visível, não a um atributo relativo.**
"Pele mais clara" é comparativo — o modelo pode atribuir a qualquer um dos dois, ou unificar.
Vestuário é binário e visível:

> punho de casaco camelo nos dois pulsos dela, à esquerda · antebraço nu e camiseta escura
> dele, à direita

Vale para distinguir pessoas, mãos, membros e qualquer par que não possa se confundir.

**3. Escala: escreva em fração de quadro, não em milímetros.**
"Plano médio aberto, 35 mm" não tem consequência em pixel — o modelo não tem sensor. O que
funciona:

> vista dos joelhos para cima · ocupando cerca de um terço da largura do quadro · com o balcão
> inteiro legível atrás · o assunto do enquadramento é a sala, não o rosto

Mantenha a lente no prompt pelo comportamento óptico que ela implica (compressão, bokeh,
distorção), mas nunca confie nela para definir enquadramento.

**4. Nunca descreva o aparato de filmagem — descreva a imagem resultante.**
"Câmera presa à bicicleta por um braço rígido" fez o modelo desenhar uma mirrorless montada
num braço, dentro do quadro. Aparato citado é aparato renderizado. Escreva o ponto de vista:

> como se o observador flutuasse um pouco à frente da bicicleta, olhando de volta para ele ·
> guidão atravessando a base do quadro em primeiríssimo plano · rosto e peito ocupando o centro

**5. Ocupar vence proibir.** "Sem faixa amarela" produziu faixa amarela; "sem logotipo"
produziu logotipos de marcas reconhecíveis. Proibição só funciona quando a coisa proibida não é exigida pela lógica
da cena — copo sem tipografia é fácil, ciclista numa avenida sem marcação de asfalto briga com
o próprio cenário. Descreva o que **deve** estar no lugar:

> faixa de ciclovia pintada de vermelho com pictograma branco de bicicleta, linha branca
> contínua e meio-fio separando da pista · camisa de ciclismo lisa, cor sólida, sem estampa,
> sem escudo, sem bandeira

**Consequência de fluxo:** não existe "corrigir" uma imagem gerada — cada regeração é um
sorteio novo da cena inteira com um prompt melhor. Espere perder acertos anteriores a cada
passada. É por isso que âncoras (folha de personagem, folha de produto) existem: o rosto e o
objeto sobrevivem ao sorteio, o resto não.

**Atalho de consistência sem bíblia.** Para uma sequência curta, ligar a saída do primeiro
plano como referência do segundo entrega o mesmo rosto, roupa e equipamento sem precisar de
folha de personagem. Para sequências longas ou
produção, a folha continua sendo o certo.

## Qual modelo para quê

Comparação do mesmo prompt em modelos diferentes:

- **Gerar → `seedream-5-pro`.** Obedeceu a trava de lado do quadro, respeitou enquadramento e
  entregou textura de pele com poro.
- **Editar → `imagen-nano-banana-2` (Pro).** Foi o único que removeu um elemento preservando
  o resto da imagem, inclusive detalhes não mencionados como uma lupa no olho.
- **Nano Banana Pro para geração do zero:** cortou a cabeça do sujeito na borda, ignorou a
  trava de lado do quadro e achatou a textura. Não é o caminho para text-to-image.

## Higiene de node

- **Confira o node depois de gravar.** Prompt salvo truncado no meio da frase acontece, com
  a ferramenta reportando sucesso. Ler o node de volta é o único jeito
  de saber.
- **Trocar de modelo pede node novo, nunca sobrescrita.** Sobrescrever destrói a comparação e
  mistura duas variáveis — prompt novo e modelo novo — sem como saber qual causou a diferença.
  Mantenha o par lado a lado com prompt idêntico.

## Parâmetros que não existem

Circula muito material de prompt com sintaxe fictícia, herdada de ferramentas fora deste
stack — sobretudo convenções de Midjourney. Nunca copie prompt de fonte assim. Não reintroduza:

| Não existe | Faça isto |
| --- | --- |
| `--texture-solver:maximum` | descrever: poros visíveis, micro-pelos, textura epidérmica em macro, sem suavização |
| `--style raw` | descrever: pele sem retoque, imperfeições naturais, realismo documental |
| `--sref` / `--oref` | `references[]` com `type: style` / `character` / `product` |
| `--v 7` | escolher pelo slug |
| `--camera-movement:` | valor do enum `cameraMotion` |
| `--motion-scale: [1-10]` | escolha do movimento + descrição de intensidade |
| `--shutter-speed: 1/50` | `lowShutter` no enum, "180° shutter" na descrição |
| `Physical Accuracy: ON` | descrever: inércia real, câmera com peso e massa, sem aceleração digital |

## Engenharia reversa de referência

Para decupar uma peça existente, trabalhe por protocolo: inventário do que se vê, plano a plano,
antes de qualquer interpretação de intenção.

Portão obrigatório antes de qualquer análise: declare se você **vê os frames**. Se não vê, não
invente cenário, enquadramento, cor, câmera nem expressão — marque tudo como INFERÊNCIA
PROVÁVEL ou CONFIRMADO PELA TRANSCRIÇÃO. Quando houver arquivo de vídeo local, extraia frames
com ffmpeg e analise a evidência; não infira o que dá para ver.
