> ## ⚠️ ARQUIVO EM QUARENTENA — NÃO USE PARA ESCOLHER MODELO
>
> Este é o roteamento de modelos do handbook Magnific (jul/2026 v1.2). Ele **não
> corresponde ao catálogo da conta do usuário** e contradiz teste próprio dele:
>
> | Este arquivo diz | O que vale (`00-execucao-magnific.md`) |
> |---|---|
> | Seedance **2.5** | Seedance **2.0** — `bytedance-seedance-pro-2.0` |
> | Padrão de imagem: **Nano Banana 2** | Padrão de imagem: **`seedream-5-pro`** |
> | Nano Banana Pro para hero difícil | Nano Banana Pro **falha em text-to-image** (teste 12/08/2026: cortou a cabeça, ignorou a trava de lado do quadro, achatou textura). É o melhor para **edição**. |
>
> **Slug, versão, limite de duração, tipo de referência e parâmetro vêm sempre de
> `00-execucao-magnific.md`, revalidado com `video_models_list` / `images_models_list`.**
>
> Guarde este arquivo apenas para o *raciocínio comparativo* entre famílias de modelo
> (o que um modelo de controle faz vs um modelo estético). Nunca copie um nome de modelo
> daqui para uma chamada real.

---

# Model Routing

Fonte: The Prompting Handbook (Magnific, jul/2026 v1.2), Parte 01 e 02.

## Modelos de imagem

| Modelo | Melhor para | Referências aceitas | Resolução máx. |
|---|---|---|---|
| **Nano Banana Pro** (Google · Gemini 3 Pro) | Trabalho cinematográfico e estético, os prompts mais difíceis, imagem hero | Estilo, personagem, produto, imagem | 4K |
| **Nano Banana 2** (Google · Gemini 3.1 Flash) | Edição, trabalho de produto e marca, iteração em alto volume | Estilo, personagem, produto, imagem | 4K |
| **Seedream 5.0** (ByteDance) | Pôsteres, embalagens, e-commerce, lotes consistentes de marca | Estilo, personagem, produto, imagem (até 10) | 4K |
| **GPT Image 2** (OpenAI) | Design com muito layout, infográficos, visuais com texto preciso | Estilo, personagem, produto, imagem | 4K |
| **Recraft V4.1** (Recraft) | Logos, ícones, assets vetoriais, sistemas de design on-brand | Estilo | SVG · 2K |
| **Flux.2** (Black Forest Labs) | Cor de marca exata, briefings estruturados tipo shot-list | Estilo, personagem, produto, imagem (até 10) | 2K |
| **Krea 2** (Krea) | Looks estético-first a partir de referências de estilo/moodboards | Estilo, imagem | 2K |

### Lógica de escolha (imagem)
- **Nano Banana 2** é o modelo mais novo e resolve a maioria dos trabalhos do dia a dia: qualidade próxima do Pro, mais rápido, texto confiável, melhor consistência multi-referência. É o padrão para edição, produto e marca.
- **Nano Banana Pro** é a escolha premium quando você precisa de precisão, precisão de marca, ou está refinando os prompts mais difíceis. Demora mais para processar mas tipicamente chega a um resultado final de maior fidelidade. Os dois custam o mesmo por imagem — roteie por comportamento, não por preço.
- **GPT Image 2** é o melhor para designs complexos focados em layout.
- **Recraft** ganha seu lugar para pôsteres dependentes de tipografia e ilustração nível escola-de-arte, e é a única opção atual que exporta arquivos vetoriais.
- **Flux.2** é construído para controle. Aceita até dez referências de uma vez, casa cores hex exatas, e segue prompts estruturados tipo shot-list — serve para pipelines de marca/produto travados. Dê um briefing explícito; um prompt vago retorna uma imagem polida mas genérica.
- **Krea 2** é construído para estilo. Trabalha a partir de referências de estilo e moodboards e produz looks que evitam o polish padrão de IA. A troca é precisão: Krea 2 interpreta o briefing em vez de segui-lo à risca, e é fraco em texto na imagem.

## Modelos de vídeo

| Modelo | Inputs (multimodal) | Áudio nativo | Resolução máx. | Melhor para |
|---|---|---|---|---|
| **Seedance 2.5** (ByteDance) | Texto, imagem, vídeo, áudio (até 50 referências mistas de imagem e vídeo, mais áudio), além de personagem, produto, estilo | Sim · lip-sync | 30s · 4K | O padrão; melhor qualidade e estética, referências, áudio, narrativa |
| **Kling 3.0 Omni** (Kuaishou) | Texto, imagem, vídeo (clonagem de performance de rosto e voz) | Sim · lip-sync | 15s · 4K | Continuidade de personagem, ação, diálogo, texto em produto preciso |
| **Happy Horse 1.1** (Alibaba) | Texto, imagem (até 9); edição vídeo-a-vídeo e troca de sujeito | Sim · lip-sync | 15s · 1080p | Curta-metragem cinematográfico, retrato/talking-head, iteração rápida |
| **Gemini Omni Flash** (Google · novo) | Texto, imagem, vídeo (input de áudio ainda não) | Sim · só voz própria | 10s · 720p | Direção conversacional; equipara ao Seedance em aderência, fica atrás em qualidade |

### Lógica de escolha (vídeo)
- **Seedance 2.5** é o padrão para qualquer coisa que vai ao ar. Tem a melhor qualidade e estética, áudio nativo, e clipes de até 30 segundos. Seu sistema de referências aceita até cinquenta imagens e vídeos num único prompt.
- **Gemini Omni Flash** equipara ao Seedance em aderência ao prompt mas fica claramente atrás em qualidade e visual (também gera seu próprio som e fala, mas não sincroniza lábios a um arquivo de áudio que você fornece): dirija de forma solta ali, finalize no Seedance.
- **Kling 3.0 Omni** ganha seu lugar quando clonagem de performance, física ou texto em produto carregam o plano; **Happy Horse** quando o orçamento é apertado.
- Sora 2 e a linha Wan completam o campo mais amplo, mas não são cobertos em detalhe neste guia.

Custos de crédito mudam com modelos e planos — ver magnific.com/pricing para preços atuais.
