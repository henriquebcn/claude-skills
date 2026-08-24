# claude-skills

Marketplace de skills para [Claude Code](https://claude.com/claude-code).

## Instalar

```
/plugin marketplace add henriquebcn/claude-skills
/plugin install fotografia-ia@henriquebcn
```

Depois, se o resumo pedir: `/reload-plugins`.

Para atualizar mais tarde: `/plugin marketplace update henriquebcn`.

## `fotografia-ia`

Diretor de fotografia e supervisor de geração audiovisual com IA generativa. Aciona sozinho
quando o pedido envolve imagem ou vídeo gerado — "monta a decupagem", "prompt pra esse plano",
"essa geração ficou errada", "analise essa referência". Ou direto:

```
/fotografia-ia:diretor-de-fotografia
```

**O que ele faz:** analisa história e ponto de vista antes de recomendar câmera, lente,
iluminação ou prompt. Traz uma hierarquia de decisão de 14 passos, decupagem plano a plano com
verificação de eixo de 180°, direção de tela e continuidade fotográfica, uma estrutura de prompt
em 9 partes, diagnóstico por eixo isolado (identidade, mãos, ação, produto, câmera, luz,
continuidade, lip sync) e um portão obrigatório de revisão do prompt em português antes de
qualquer geração.

**Como entra:** com uma saudação ou um pedido vago, ele abre um card de quatro portas —
DECUPAR, CRIAR, GERAR, CONSERTAR — e espera você dizer em português o que tem na mão. Se o seu
primeiro pedido já for específico, ele pula o card e entra direto no trabalho. Toda resposta de
trabalho fecha com uma régua mostrando em que etapa do pipeline você está.

**Conteúdo:** espinha de decisão + 17 bases de referência carregadas sob demanda:

| Faixa | O que é |
| --- | --- |
| `00` | camada de execução — catálogo e slugs, enum real de movimento de câmera, referências, keyframes, multishot, fluxo MCP |
| `10`–`12` | craft — fundamentos, avançado, e IA generativa |
| `20`–`22`, `24` | doutrinas de plano único (Cinema Master Engine, Grace Cinema Shot) e dado de obturador |
| `23` | protocolo de engenharia reversa em 21 seções — o motor da porta DECUPAR |
| `30`–`34` | Magnific Prompting Handbook absorvido |
| `40`–`41` | Seedance Director Pro absorvido |
| `50` | Image Architect absorvido |

### Antes de usar

A camada de execução (`references/00-execucao-magnific.md`) traz um catálogo de modelos que
reflete um plano específico num dado momento. **Slugs e limites mudam.** Revalide com
`video_models_list` e `images_models_list` antes de tratar qualquer número como atual — se o seu
plano libera outros modelos, os slugs não vão bater.

### O que foi absorvido, e como

Três skills públicas estão **embutidas aqui**, não referenciadas — você não precisa instalar
nada ao lado:

| Origem | Vira | O que fica |
| --- | --- | --- |
| `magnific-prompting-guide` | `30`–`33` | blocos injetáveis, as cinco costuras, doze movimentos, física de cena |
| `seedance-director-pro` | `40`–`41` | arquétipos de cena, timeline de efeitos, densidade, arco de energia |
| `image-architect` | `50` | modos de análise, território visual, moldura de seis dimensões |

Absorver não é copiar. Cada arquivo abre com um cabeçalho de precedência declarando o que nele
**vale** e o que está **revogado** — porque as três discordam entre si e com o catálogo
verificado da conta. O que foi revogado:

- **roteamento de modelo** nas três — slug e limite vêm sempre da faixa `00`;
- **a saída obrigatória em JSON só-ZH** do Seedance — ela proibiria o portão de revisão do
  prompt em português, que aqui é regra dura;
- **os orçamentos de token e a proibição de bullets** do Image Architect — o formato de resposta
  é o da espinha;
- **o catálogo de modelos** do handbook da Magnific, preservado em `34` apenas como prova de
  por que é inválido.

Nenhuma fonte absorvida revoga o portão de revisão em português.

## Licença

MIT. As bases de conhecimento são material autoral do mantenedor.
