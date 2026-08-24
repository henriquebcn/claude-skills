> **Precedência:** use este arquivo pelo **método** (estrutura de prompt, costuras,
> movimentos, linguagem de lente, workflows). Onde ele nomear modelo ou versão, ignore —
> slug, versão e limites vêm de `00-execucao-magnific.md`.

---

# Video Techniques

Fonte: The Prompting Handbook (Magnific, jul/2026 v1.2), Parte 02 — Prompting for Video.

O salto de 2026 é a mudança para arquiteturas unificadas "omni": texto, imagem, vídeo e áudio entram num único modelo, e sai footage finalizado com som sincronizado, num único passo.

## Seis conceitos-chave

1. **Multi-modal ("omni")** — um modelo ingere texto, imagens, vídeo e áudio juntos e produz vídeo com som num único passo. Esse design de passo único é a maior mudança em relação à geração anterior de motores de vídeo, que pegava um prompt de texto e devolvia imagem muda.
2. **Áudio nativo** — diálogo, efeitos e som ambiente são gerados junto com a imagem e travados a ela, em vez de adicionados na pós-produção, incluindo fala com lip-sync.
3. **Start/end frame** — forneça um primeiro frame (e opcionalmente um último) e o modelo anima o movimento entre eles, dando controle preciso sobre como um plano abre e pousa.
4. **Referências** — referências de imagem fixam um personagem ou produto; referências de vídeo ensinam movimento e voz; referências de áudio definem uma voz ou paisagem sonora.
5. **Storyboarding multi-shot** — vários cortes são gerados num único job com continuidade, cada plano carregando seu próprio prompt de duração, enquadramento e ação.
6. **Consistência de personagem** — "Elements" e coreferência travam identidades para que múltiplos personagens permaneçam distintos e on-model ao longo de cada plano e mudança de cena.

## Start/end frame vs. referências (frequentemente confundidos)

Esses dois controles são fáceis de confundir, mas respondem perguntas diferentes — e você pode usar ambos na mesma geração.

- **Start/end frame: controla o momento.** Você fixa o primeiro frame (e opcionalmente o último) de um único plano, e o modelo gera o movimento entre eles. Eles governam como *este* clipe específico abre e pousa. Um plano diferente significa frames diferentes.
- **Referências de imagem: controlam a identidade.** Você mostra ao modelo como é um personagem, produto ou estilo, para que ele permaneça consistente em qualquer ponto da timeline e ao longo de vários planos. Elas não fixam um momento; informam aparência.

**Em resumo:** start/end frames decidem onde o plano começa e termina; referências decidem quem ou o quê aparece, e em qual estilo. Fixe um start frame para controlar a composição de abertura, e anexe uma referência de personagem para que ele permaneça on-model, na mesma geração.

## Estrutura de prompt de vídeo

Todos os quatro modelos principais suportam texto-para-vídeo e imagem-para-vídeo; referência-para-vídeo e frame-para-vídeo variam por modelo (ver `model-routing.md`). O prompt é uma descrição de plano, não uma sacola de tags: pense como um diretor passando instruções para uma equipe de câmera.

| Parte | O que responde | No prompt |
|---|---|---|
| Plano | O enquadramento | plano médio vertical 9:16 |
| Movimento de câmera | Um movimento por clipe | push-in rápido |
| Sujeito | Quem ou o quê | uma mão e um frasco de café |
| Ação | Uma ação por clipe | levanta o frasco do balcão |
| Cenário | Onde, e quando | balcão de cozinha ensolarado, manhã |
| Luz | Nomeie o tipo de luz | luz natural brilhante de manhã |
| Estilo | O acabamento | limpo e arejado |
| Áudio | O que se ouve | SFX: derramamento suave; sem música, sem legendas |

**Ordem específica por modelo:**
- **Seedance:** declare planos, duração e proporção logo de início, depois sujeito → ação → ambiente → câmera → estilo; rotule referências como @image1 / @video1 / @audio1.
- **Kling:** sujeito + movimento + cena + câmera + iluminação + atmosfera.
- **Happy Horse:** segue a mesma disciplina de descrição de plano.
- **Gemini Omni Flash:** é a exceção — ajustado para direção conversacional, então você pode dar o prompt de forma solta e refinar em turnos seguintes.

**Regras:**
- **Front-load o plano.** Abra com o tipo de plano e um movimento de câmera; o modelo lê a primeira linha primeiro.
- **Uma ação, um movimento de câmera por clipe.** Empilhar qualquer um dos dois produz distorção e instabilidade.
- **Use linguagem real de cinematografia.** "Slow dolly-in," fontes de luz nomeadas, tamanhos de plano exatos. Movimentos concretos e luz nomeada batem palavras de humor vagas, e números de lente quase não registram.
- **Controle o áudio.** SFX e ambiente em palavras simples, diálogo entre aspas. Escreva "No music" para ter SFX limpo apenas (a trilha é adicionada depois na edição), e "no subtitles" para evitar legendas queimadas.
- **Repita o copy de produto literalmente.** Qualquer texto na embalagem ou na tela deve ser citado no prompt, exatamente como deve ser lido, tanto em vídeo quanto em imagem. Kling 3.0 é o mais forte em manter o copy de produto correto em movimento.
- **Para imagem-para-vídeo, descreva só movimento e câmera** — o frame já fornece o sujeito.
- **Itere barato, finalize nítido.** Trave a composição em 720p/1080p, depois re-renderize o resultado escolhido em 4K.

**Por que quase todo prompt termina "No music. No subtitles.":** música gerada te trava numa escolha, e legendas queimadas não podem ser removidas depois. Gere limpo — SFX e ambiente apenas, legendas desligadas — e adicione trilha e tipografia na edição, onde você as controla. Se um clipe carrega diálogo, mantenha "no subtitles" e deixe a fala viver entre aspas.

## Edição de vídeo

A edição é onde a divisão geração-versus-refinamento aparece. Modelos de geração (Seedance 2.5, Happy Horse) são mais fortes quando você cria um clipe novo e o impacto visual importa mais. Modelos de edição (Kling 3.0 Omni, Gemini Omni Flash) são mais fortes quando você muda um clipe existente e a fidelidade à filmagem original importa mais. Escore a música por último; deixe-a de fora no momento da geração.

Operações mais comuns:
- **Vídeo-a-vídeo & restyle:** re-peliculagem/remasterização de filmagem existente. O pipeline de edição do Kling 3.0 Omni roda 3–15s em 4K entrando e saindo, mantendo fidelidade à fonte.
- **Extensão:** encadeie gerações (cada novo clipe continua do último frame do anterior) para ultrapassar a duração base; Seedance e Kling estendem um plano no lugar mantendo continuidade visual.
- **Reframe & upscale:** mude a proporção para uma nova plataforma, e faça upscale para entrega — os modelos de geração alcançam 4K nativamente, ferramentas dedicadas de upscale chegam a 8K.
- **Edições de voz & áudio:** troque ou dublê a voz falada preservando timing e visuais, ou adicione a música que você segurou no momento da geração.

**Gemini Omni Flash — o modelo re-deriva a física:** peça para transformar uma mesa em uma piscina rasa e ele raciocina sobre a cena inteira: a mão passa a ler como molhada, água ondula e refrata, sombras e reflexos se atualizam, e os efeitos sonoros seguem. Essa consistência física é o que o torna forte dentro de pipelines de edição.

**Gemini Omni Flash — o modelo escuta a filmagem:** ele consegue agir sobre a fala dentro do clipe: o próprio áudio do vídeo vira parte da instrução. Aponte para uma linha de diálogo e deixe que ela dirija a edição, sem transcrição manual.

## Pipeline: reescrever o primeiro frame

As edições de vídeo mais fortes muitas vezes nem são feitas num modelo de vídeo. Como um clipe é conduzido pelo seu start frame, você pode puxar o frame um de qualquer vídeo, editá-lo como uma imagem com Nano Banana Pro (onde o controle é cirúrgico), e devolvê-lo ao Seedance 2.5 com o clipe original como referência de movimento. O resultado: o mesmo plano, o mesmo movimento, o mesmo ritmo, com a mudança que você dirigiu.

**Por que funciona:** o start frame fixa o que o plano abre; a referência de vídeo fixa como ele se move. Dividir a edição assim dá controle de nível imagem sobre o conteúdo e continuidade de nível vídeo sobre o movimento — e encadeia: edite qualquer frame, estenda a partir dele, ou re-estilize uma sequência inteira um start frame de cada vez.

**Passos:**
1. **Comece com um clipe** — qualquer clipe funciona, gerado ou filmado.
2. **Extraia o frame um** — exporte o primeiro frame como still. No Magnific o start frame de toda geração já fica salvo junto ao clipe.
3. **Edite o frame com Nano Banana Pro** — faça a mudança como uma edição de imagem, onde seguir instruções é mais forte. Nomeie o que muda; fixe o resto.
   ```
   @image1 Change the [objeto] to [mudança]; keep the [elemento fixo A], the [elemento fixo B], the camera angle and everything else exactly.
   ```
4. **Re-renderize com Seedance 2.5** — defina o frame editado como start frame e anexe o clipe original como referência de movimento: o plano repete seu próprio movimento em torno do novo sujeito.
   ```
   @image1 @video1 Repeat the exact same [movimento de câmera] as @video1, now around the [novo sujeito] from the start frame. Same pacing, same framing, one continuous take. No cuts.
   ```

## Pipeline: cobertura de um local, todos os ângulos

Um único still de um local pode virar cobertura completa de cena. Solte a imagem no Seedance 2.5 (ou Kling em 4K) como start frame e dê o prompt de um voo lento que gira e segura em cada ângulo. Nomeie cada rotação com um ponto de parada — ex.: "rotates right and slowly pushes in over the crowd toward the floodlit pitch, then rotates left and slowly pushes in along the rows of cheering fans close to the lens, then rotates 180 degrees and slowly pushes in toward the upper tier" — em vez de pedir "múltiplos ângulos" genericamente.

**Por que funciona:** nomear cada rotação e dar a ela uma parada é o que torna os frames extraíveis. E porque cada ângulo vem de um único render contínuo, a multidão, a luz e a arquitetura permanecem consistentes ao longo de todos eles — algo que gerar cada ângulo como uma imagem separada não consegue garantir. Os beats mantidos são frames extraíveis (luz combinando, cenário combinando), prontos para servir como start frames, referências ou backdrops para os planos reais.
