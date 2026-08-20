# Base operacional — Cinematografia para IA generativa

## Finalidade

Esta base traduz decisões de direção de fotografia para geração de imagens e vídeos com IA. Ela deve ser usada depois da análise narrativa e cinematográfica, nunca como substituta dessa análise.

Modelos-alvo desta versão:

- geração de imagens estáticas;
- Kling VIDEO 3.0 e 3.0 Omni;
- Kling 3.0 Motion Control;
- Seedance 2.0;
- Veo 3.1.

Data de referência das capacidades: 11 de agosto de 2026. Como recursos, interfaces e limites mudam, o futuro agente deve verificar documentação oficial quando a resposta depender de disponibilidade atual.

## Sumário

1. Princípio de funcionamento
2. Pipeline universal
3. Hierarquia de referências
4. Arquitetura universal de prompt
5. Geração de imagens estáticas
6. Image-to-video
7. Start frame e end frame
8. Vídeo de referência e Motion Control
9. Multi-shot
10. Continuidade de identidade, produto e cenário
11. Movimento humano natural
12. Movimento de câmera executável
13. Áudio, fala e lip sync
14. Adaptador Kling 3.0
15. Adaptador Seedance 2.0
16. Adaptador Veo 3.1
17. Escolha do modelo
18. Diagnóstico de falhas
19. Estratégias de correção
20. Controle de custo e iteração
21. Formatos de saída do agente
22. Regras de atualização

---

## 1. Princípio de funcionamento

O agente deve separar cinco operações:

1. compreender a cena;
2. projetar a cinematografia;
3. escolher a modalidade de geração;
4. traduzir o plano para o modelo escolhido;
5. analisar o resultado e corrigir somente a causa provável.

Uma descrição extensa não compensa uma imagem-base inadequada, referências conflitantes ou uma ação complexa demais para a duração disponível.

---

## 2. Pipeline universal

### Etapa 1 — Entrada

Receber um ou mais itens:

- roteiro;
- storyboard;
- imagem inicial;
- imagem final;
- character sheet;
- produto;
- vídeo de movimento;
- áudio ou fala;
- referência de estilo;
- vídeo gerado com erro.

### Etapa 2 — Diagnóstico narrativo

Identificar:

- beat;
- ação principal;
- emoção;
- ponto de vista;
- mudança entre início e fim;
- duração realista.

### Etapa 3 — Plano cinematográfico

Definir:

- escala e ângulo;
- lente ou comportamento óptico;
- posição e movimento de câmera;
- blocking;
- luz;
- foco;
- ritmo;
- quadro inicial e final.

### Etapa 4 — Modalidade

Escolher:

- text-to-image;
- image-to-image;
- text-to-video;
- image-to-video;
- first-and-last-frame;
- referência de personagem/elemento;
- vídeo de movimento;
- multi-shot;
- extensão ou continuação.

### Etapa 5 — Geração

Escrever prompt compatível com o modelo, anexar somente referências necessárias e configurar duração, proporção e áudio.

### Etapa 6 — Avaliação

Comparar resultado com critérios prévios:

- identidade;
- ação;
- naturalidade;
- câmera;
- continuidade;
- produto;
- luz;
- duração;
- áudio.

### Etapa 7 — Correção

Alterar uma variável causal por vez quando possível. Preservar o que funcionou.

---

## 3. Hierarquia de referências

### 3.1 Referências podem competir

Cada referência deve ter uma função explícita:

- identidade;
- figurino;
- produto;
- cenário;
- composição;
- estilo;
- movimento;
- áudio;
- quadro inicial;
- quadro final.

Não anexar duas fontes divergentes para a mesma função sem explicar a prioridade.

### 3.2 Ordem de prioridade recomendada

1. imagem inicial/final que define geometria do plano;
2. referência oficial de personagem ou produto;
3. referência de movimento;
4. cenário;
5. iluminação e estilo;
6. descrição textual complementar.

A prioridade efetiva depende do modelo. O agente deve deixar claro o que a plataforma tratará como frame, elemento ou referência.

### 3.3 Referência mínima suficiente

Mais referências não significam maior controle. Usar o menor conjunto que represente completamente os elementos críticos.

---

## 4. Arquitetura universal de prompt

Organizar nesta ordem:

1. **Plano:** escala, ângulo e posição.
2. **Sujeito:** identidade, aparência e elementos invariáveis.
3. **Ação:** uma sequência temporal clara.
4. **Performance:** emoção, ritmo e microcomportamentos.
5. **Câmera:** movimento, velocidade, estabilidade e ponto final.
6. **Ambiente:** elementos necessários e continuidade.
7. **Luz e cor:** motivação, contraste e atmosfera.
8. **Áudio:** fala, voz, ambiente e efeitos, quando suportado.
9. **Restrições:** o que não pode mudar ou aparecer.

### Estrutura temporal

Para ações complexas, usar beats:

- início;
- desenvolvimento;
- conclusão.

Exemplo abstrato:

> A personagem começa com as duas mãos apoiando o telefone. Ela afrouxa os dedos da mão direita, transfere o peso do aparelho para a esquerda e só então baixa a mão direita. O telefone permanece estável e com a mesma orientação durante toda a ação.

Essa escrita descreve causalidade física, não apenas o resultado.

### Restrições úteis

Restringir:

- mudanças de identidade;
- membros extras;
- deformações;
- objetos que surgem;
- troca de figurino;
- alteração de marca;
- movimento de câmera não solicitado;
- corte quando o plano deve ser contínuo.

Evitar listas negativas enormes; elas podem competir com a ação principal.

---

## 5. Geração de imagens estáticas

### 5.1 Função da imagem-base

Em image-to-video, a imagem inicial já define grande parte de:

- identidade;
- anatomia;
- figurino;
- cenário;
- luz;
- perspectiva;
- lente aparente;
- composição;
- posição dos objetos.

Corrigir esses problemas na imagem antes de animá-la costuma ser mais eficiente do que tentar corrigi-los no prompt de vídeo.

### 5.2 Prompt de imagem

Incluir:

- sujeito e ação congelada;
- momento exato;
- plano e ângulo;
- posição de câmera;
- distância focal ou descrição óptica;
- composição;
- blocking;
- luz;
- cenário;
- paleta e textura;
- proporção;
- invariantes de marca e personagem.

### 5.3 Preparação para animação

A pose inicial precisa permitir a ação seguinte. Evitar:

- mãos ocultas quando serão protagonistas;
- objetos fundidos ao corpo;
- interseções ambíguas;
- membro fora do quadro se precisará entrar imediatamente;
- pose extrema sem trajetória possível;
- composição sem espaço para o movimento.

---

## 6. Image-to-video

### 6.1 Regra principal

Descrever transformação e movimento, não redescrever excessivamente o que já existe na imagem.

### 6.2 Elementos do prompt

- estado inicial já visível;
- ação principal;
- ordem física dos movimentos;
- performance;
- câmera;
- estado final;
- invariantes.

### 6.3 Complexidade por duração

Quanto menor a duração, menor deve ser o número de ações independentes. Um plano curto funciona melhor com uma ação dominante e microações complementares.

### 6.4 Câmera e sujeito

Evitar solicitar simultaneamente:

- ação corporal complexa;
- manipulação delicada de objeto;
- grande mudança de expressão;
- câmera orbital;
- rack focus;
- transformação de cenário.

Dividir em planos quando a carga de controle for alta.

---

## 7. Start frame e end frame

### 7.1 Quando usar

Usar para:

- deslocamento entre poses plausíveis;
- aproximação ou afastamento controlado;
- transformação visual;
- transição espacial;
- continuidade entre estados;
- fechamento em composição obrigatória.

### 7.2 Compatibilidade geométrica

Os frames devem ser compatíveis em:

- identidade;
- figurino;
- cenário;
- luz;
- proporção;
- lado do eixo;
- posição relativa de objetos;
- escala e perspectiva, salvo quando a mudança é intencional.

### 7.3 Corte versus interpolação

Se o objetivo é um corte seco entre duas câmeras, não pedir ao modelo para interpolar fisicamente entre ângulos incompatíveis. Usar multi-shot/corte explícito ou gerar os planos separadamente.

### 7.4 Caminho intermediário

Descrever como o estado inicial deve chegar ao final. Sem trajetória clara, o modelo pode inventar ações, deformações ou cenários intermediários.

---

## 8. Vídeo de referência e Motion Control

### 8.1 Função

Transferir movimento, ritmo, expressão ou coreografia de uma performance de referência para um personagem-alvo.

### 8.2 Compatibilidade

Buscar correspondência entre referência e personagem em:

- corpo visível;
- orientação;
- escala no quadro;
- proporções;
- câmera fixa ou móvel;
- duração;
- contato com objetos;
- quantidade de pessoas.

### 8.3 Vídeo limpo

Preferir:

- sujeito claramente visível;
- pouca oclusão;
- movimento completo;
- início e fim estáveis;
- câmera coerente;
- resolução suficiente;
- ausência de cortes escondidos.

### 8.4 Interação com objetos

Movimento corporal pode transferir melhor do que contato preciso com telefone, roupa, ferramenta ou produto. Para objetos críticos, criar imagem-base compatível e reduzir a amplitude do gesto.

---

## 9. Multi-shot

### 9.1 Quando usar

- diálogos;
- mudança clara de ponto de vista;
- progressão de aberto para fechado;
- ações paralelas;
- cobertura curta com continuidade;
- plano e contraplano.

### 9.2 Quando gerar separadamente

- identidade ou produto precisam de máxima fidelidade;
- ângulos são muito diferentes;
- cada plano exige controle preciso;
- uma falha obrigaria regenerar toda a sequência;
- a montagem pode ser feita externamente.

### 9.3 Descrição

Numerar planos e definir para cada um:

- duração aproximada;
- enquadramento;
- ação;
- câmera;
- fala/som;
- transição.

---

## 10. Continuidade de identidade, produto e cenário

### 10.1 Character Bible

Registrar invariantes:

- estrutura facial;
- cabelo;
- pele;
- olhos;
- proporções;
- idade aparente;
- figurino;
- acessórios;
- voz e comportamento.

### 10.2 Product Bible

Registrar:

- geometria;
- logotipo;
- texto;
- cores;
- materiais;
- escala;
- orientação;
- áreas que podem ser ocultadas;
- áreas que precisam permanecer legíveis.

### 10.3 Environment Bible

Registrar:

- arquitetura;
- objetos fixos;
- geografia;
- hora;
- direção de luz;
- clima;
- paleta;
- profundidade e fundo.

### 10.4 Continuidade entre gerações

Reutilizar:

- referências aprovadas;
- descrição invariável;
- formato e proporção;
- comportamento de lente;
- luz;
- frames finais como novos frames iniciais, quando apropriado.

Não confiar apenas em repetir o mesmo texto.

---

## 11. Movimento humano natural

### 11.1 Cadeia física

Descrever preparação, ação e acomodação:

1. antecipação;
2. deslocamento principal;
3. transferência de peso;
4. reação de membros e roupa;
5. estabilização final.

### 11.2 Microcomportamentos

Usar com moderação:

- respiração;
- piscadas;
- pequenos ajustes posturais;
- mudança gradual de olhar;
- microexpressões;
- balanço secundário do corpo.

### 11.3 Manipulação de objetos

Especificar:

- qual mão sustenta;
- pontos de contato;
- ordem dos dedos;
- transferência de peso;
- orientação do objeto;
- estado final.

### 11.4 Velocidade

Palavras como “natural” são insuficientes. Definir se o gesto é lento, deliberado, hesitante, contínuo, leve ou enérgico e indicar a ordem temporal.

---

## 12. Movimento de câmera executável

### 12.1 Um movimento dominante

Em planos curtos, preferir um movimento principal:

- dolly in suave;
- truck lateral;
- pan de acompanhamento;
- tilt de revelação;
- arco curto;
- câmera fixa;
- handheld controlada.

### 12.2 Descrever trajetória

Incluir:

- direção;
- distância relativa;
- velocidade;
- estabilidade;
- alvo;
- início e parada;
- composição final.

### 12.3 Evitar conflito

Não pedir “câmera completamente estática” e “aproximação cinematográfica” no mesmo plano. Não combinar dolly, zoom, pan e órbita sem necessidade.

### 12.4 Movimento virtual e física

Movimentos amplos exigem que o modelo invente áreas não presentes na imagem. Quanto maior a revelação, maior o risco de mudança de cenário, anatomia ou produto.

---

## 13. Áudio, fala e lip sync

### 13.1 Separar camadas

- fala;
- voz e interpretação;
- ambiente;
- efeitos;
- música;
- silêncio intencional.

### 13.2 Fala

Fornecer texto exato, idioma e variedade linguística. Definir emoção, ritmo, volume e pausas sem sobrecarregar a atuação.

### 13.3 Lip sync

Priorizar:

- rosto visível;
- ângulo favorável;
- pouca oclusão;
- duração suficiente;
- fala compatível com o tempo;
- expressão que não contradiga a locução.

### 13.4 Estratégia de segurança

Quando fidelidade do texto for indispensável, considerar gerar vídeo sem fala e realizar voz/lip sync em etapa dedicada, conforme a capacidade real da ferramenta.

---

## 14. Adaptador Kling 3.0

### 14.1 Capacidades oficiais relevantes

Kling VIDEO 3.0 oferece text-to-video, image-to-video, start/end frames, áudio nativo, multi-shot, referências de elementos e duração flexível de até 15 segundos. A plataforma também apresenta consistência de múltiplos sujeitos e fluxo específico de Motion Control.

### 14.2 Pontos fortes operacionais

- image-to-video com controle por frame;
- Element/Subject consistency;
- multi-shot automático ou customizado;
- Motion Control com vídeo de ação;
- áudio nativo e diálogo em modalidades suportadas;
- narrativa curta com vários planos.

### 14.3 Estratégia de prompt

Para plano único:

1. reconhecer que a imagem já define o visual;
2. descrever ação em ordem;
3. descrever câmera;
4. fixar invariantes;
5. indicar estado final.

Para multi-shot:

1. habilitar modalidade correspondente;
2. numerar planos;
3. manter uma ação e intenção por plano;
4. definir corte, não interpolação, quando houver troca de câmera;
5. repetir elementos críticos de continuidade.

### 14.4 Motion Control

Usar vídeo com performance limpa e imagem de personagem compatível. O guia oficial do Kling 3.0 descreve vínculo de elemento facial para reforçar consistência em movimentos complexos e múltiplos ângulos.

### 14.5 Riscos

- mudança de mãos e objetos em gestos delicados;
- câmera adicional inventada;
- multi-shot divergindo da decupagem;
- áudio competindo com atuação;
- referências de elementos conflitantes.

---

## 15. Adaptador Seedance 2.0

### 15.1 Capacidades oficiais relevantes

Seedance 2.0 utiliza arquitetura conjunta de áudio e vídeo e aceita referências por texto, imagem, áudio e vídeo. Isso favorece composição multimodal e transferência de características entre materiais.

### 15.2 Pontos fortes operacionais

- compreensão multimodal;
- referência de vídeo para movimento ou linguagem;
- áudio integrado;
- cenas com fala e performance;
- uso combinado de imagens, vídeo e áudio.

### 15.3 Estratégia de prompt

Definir explicitamente o papel de cada anexo:

- imagem A = personagem;
- imagem B = ambiente/produto;
- vídeo C = movimento;
- áudio D = fala/ritmo.

Depois escrever:

1. plano e composição;
2. identidade;
3. ação temporal;
4. relação com referência de movimento;
5. câmera;
6. áudio;
7. invariantes.

### 15.4 Riscos

- modelo copiar também câmera ou cenário do vídeo de referência;
- excesso de referências gerar mistura;
- ação longa ultrapassar a duração;
- fala, gesto e câmera competirem;
- alteração de identidade durante mudanças de ângulo.

### 15.5 Nota de versão

Seedance 2.5 foi anunciado em julho de 2026 com capacidades ampliadas. Esta base mantém Seedance 2.0 como alvo porque faz parte do fluxo definido pelo usuário. Não transferir automaticamente limites ou recursos do 2.5 para o 2.0.

---

## 16. Adaptador Veo 3.1

### 16.1 Capacidades oficiais relevantes

Veo 3.1 oferece geração de vídeo com áudio nativo, image-to-video, extensão e controles baseados em frames e imagens de referência em modalidades suportadas.

### 16.2 Prompt recomendado

Organizar em frases claras:

1. cinematografia;
2. sujeito;
3. ação;
4. ambiente;
5. luz;
6. áudio e fala;
7. restrições.

### 16.3 Image-to-video

A documentação oficial orienta usar uma imagem próxima do quadro inicial desejado. O agente deve evitar pedir uma composição inicial incompatível com a imagem enviada.

### 16.4 Primeiro e último frame

Usar quando a modalidade e duração disponíveis suportarem a combinação. Verificar documentação atual antes de afirmar limites, pois a API e a interface podem oferecer conjuntos diferentes.

### 16.5 Riscos

- inventar conteúdo durante transições entre frames incompatíveis;
- áudio ou fala alterar performance;
- referência visual ser tratada como guia de conteúdo em vez de identidade rígida;
- extensão produzir deriva progressiva.

---

## 17. Escolha do modelo

| Necessidade dominante | Opção inicial | Motivo | Verificação necessária |
| --- | --- | --- | --- |
| Animar imagem com controle de ação | Kling 3.0 ou Veo 3.1 | Bons fluxos de image-to-video | Fidelidade de mãos e objetos |
| Transferir performance corporal | Kling Motion Control | Fluxo dedicado de movimento | Compatibilidade entre corpo e vídeo |
| Combinar imagem, vídeo e áudio | Seedance 2.0 | Arquitetura multimodal | Papel de cada referência |
| Criar vários planos curtos | Kling 3.0 Multi-Shot | Controle nativo de sequência | Decupagem e consistência |
| Vídeo com som integrado | Veo 3.1, Kling 3.0 ou Seedance 2.0 | Áudio nativo | Idioma, duração e lip sync |
| Corte seco entre ângulos | Multi-shot ou planos separados | Evita interpolação impossível | Continuidade de personagem e cenário |
| Produto ou logotipo crítico | Imagem-base forte e plano simples | Reduz reinvenção | Legibilidade e geometria |

A tabela orienta testes, não substitui comparação atual entre versões e acesso disponível.

---

## 18. Diagnóstico de falhas

### 18.1 Identidade mudou

Causas prováveis:

- referência fraca ou distante;
- mudança extrema de ângulo;
- múltiplas identidades concorrentes;
- movimento longo;
- rosto pequeno ou oculto.

### 18.2 Mãos ou objeto deformaram

Causas:

- pose inicial ambígua;
- contato complexo;
- dedos ocultos;
- ação rápida;
- transferência de objeto mal definida;
- câmera movimentando-se ao mesmo tempo.

### 18.3 Câmera alucinou

Causas:

- movimentos conflitantes;
- descrição vaga;
- start/end frames incompatíveis;
- referência de movimento contém câmera indesejada;
- revelação ampla de áreas ausentes.

### 18.4 Ação não terminou

Causas:

- excesso de beats;
- duração curta;
- falta de estado final;
- início demorado;
- ação fisicamente complexa.

### 18.5 Movimento artificial

Causas:

- ausência de antecipação e transferência de peso;
- velocidade genérica;
- pose inicial incompatível;
- gesto descrito apenas pelo resultado;
- microações demais.

### 18.6 Produto ou logo mudou

Causas:

- produto pequeno;
- rotação excessiva;
- oclusão;
- texto muito fino;
- referência insuficiente;
- modelo precisou reconstruir área não visível.

### 18.7 Continuidade quebrou

Causas:

- frames com luz ou perspectiva diferentes;
- troca de eixo;
- referências divergentes;
- planos gerados sem Bible;
- extensão sucessiva com deriva.

---

## 19. Estratégias de correção

### Ordem recomendada

1. corrigir imagem-base;
2. reduzir ação;
3. estabilizar câmera;
4. descrever cadeia física;
5. reforçar invariantes;
6. remover referências conflitantes;
7. dividir em planos;
8. trocar modalidade;
9. trocar modelo.

### Correção mínima

Preservar trechos do prompt que funcionaram. Modificar causa provável, não reescrever todo o projeto a cada tentativa.

### Plano de recuperação

Se a ação completa falhar repetidamente:

- gerar início e conclusão como planos separados;
- ocultar a transição com corte ou insert;
- substituir contato complexo por gesto sugerido;
- usar reação antes ou depois do objeto;
- completar na montagem.

---

## 20. Controle de custo e iteração

### 20.1 Testes baratos primeiro

- menor duração compatível;
- resolução de teste, quando disponível;
- câmera simples;
- uma ação;
- ausência de áudio se ele não estiver sendo validado;
- seed/referência preservada quando a ferramenta permitir.

### 20.2 Critérios antes de gerar

Definir sucesso em ordem:

1. identidade;
2. ação;
3. objeto/produto;
4. câmera;
5. naturalidade;
6. luz e acabamento;
7. áudio.

### 20.3 Registro de tentativas

Registrar:

- modelo e versão;
- modalidade;
- duração;
- referências;
- prompt;
- resultado;
- falha dominante;
- hipótese;
- alteração seguinte;
- créditos ou custo.

---

## 21. Formatos de saída do agente

### 21.1 Recomendação de ferramenta

- necessidade;
- modelo sugerido;
- modalidade;
- justificativa;
- riscos;
- alternativa.

### 21.2 Prompt de geração

Entregar:

1. prompt principal pronto para copiar;
2. referências e função de cada uma;
3. configurações;
4. critérios de aprovação;
5. plano corretivo provável.

### 21.3 Diagnóstico de vídeo

- resultado pretendido;
- problema visível;
- causa provável;
- evidência;
- correção mínima;
- novo prompt;
- mudança de modalidade se necessária.

### 21.4 Plano de produção

- decupagem;
- imagens necessárias;
- ordem de geração;
- modelo por plano;
- estimativa de tentativas;
- checkpoints de aprovação;
- montagem final.

---

## 22. Regras de atualização

- Manter conhecimento cinematográfico universal separado dos adaptadores.
- Registrar data de verificação de cada modelo.
- Usar documentação oficial como fonte principal.
- Não atribuir a uma versão recursos anunciados para outra.
- Distinguir interface web, aplicativo e API.
- Tratar relatos de usuários como evidência de comportamento, não especificação oficial.
- Atualizar somente o adaptador afetado quando um modelo mudar.

## Referências oficiais

- [Kling — VIDEO 3.0 Model User Guide](https://app.klingai.com/global/quickstart/klingai-video-3-model-user-guide)
- [Kling — VIDEO 3.0 Motion Control](https://app.klingai.com/global/quickstart/motion-control-user-guide)
- [Kling — Image-to-Video API](https://app.klingai.com/global/dev/document-api/apiReference/model/imageToVideo)
- [ByteDance Seed — Seedance 2.0](https://seed.bytedance.com/seedance2_0)
- [ByteDance Seed — lançamento do Seedance 2.0](https://seed.bytedance.com/en/blog/official-launch-of-seedance-2-0)
- [Google AI for Developers — geração de vídeo com Veo](https://ai.google.dev/gemini-api/docs/veo)
- [Google AI for Developers — documentação de vídeo](https://ai.google.dev/gemini-api/docs/video)

## Síntese operacional

O agente deve transformar intenção narrativa em uma ação visual simples, escolher a modalidade que oferece controle real sobre os elementos críticos, atribuir função explícita a cada referência e gerar com critérios de aprovação definidos. Quando houver falha, deve diagnosticar identidade, física, câmera, continuidade, objeto, áudio e duração separadamente, corrigindo a causa dominante com a menor alteração possível.
