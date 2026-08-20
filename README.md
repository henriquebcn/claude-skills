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

**Conteúdo:** espinha de decisão + 7 bases de referência carregadas sob demanda — craft de
cinematografia (fundamentos e avançado), craft específico de IA generativa, duas doutrinas de
composição de plano único, e uma camada de execução com catálogo de modelos, enum real de
movimento de câmera, regras de referência e keyframe.

### Antes de usar

A camada de execução (`references/00-execucao-magnific.md`) traz um catálogo de modelos que
reflete um plano específico num dado momento. **Slugs e limites mudam.** Revalide com
`video_models_list` e `images_models_list` antes de tratar qualquer número como atual — se o seu
plano libera outros modelos, os slugs não vão bater.

### Complementos opcionais

Três skills públicas ampliam o craft e valem instalar ao lado — não estão embutidas aqui de
propósito, para que continuem recebendo as atualizações de seus autores:

- `magnific-prompting-guide` — blocos injetáveis, costuras de encadeamento, física de cena
- `seedance-director-pro` — arquétipos de cena, timeline de efeitos, arco de energia
- `image-architect` — modos de análise e território visual

O `SKILL.md` já diz, para cada uma, o que nelas fica revogado em favor da espinha — sobretudo
roteamento de modelo e mandatos de formato de saída, que conflitam entre si.

## Licença

MIT. As bases de conhecimento são material autoral do mantenedor.
