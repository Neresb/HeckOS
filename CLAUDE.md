# Move Academia Personalizada — HeckOS

Operação de conteúdo e marketing da Move Academia Personalizada
(Medianeira/PR). Essa pasta representa o negócio da Move — memória,
tom de voz e identidade visual são todos dela.

## O que é esse workspace

Operação da Move Academia. O foco principal hoje é conteúdo (posts,
carrosséis, campanhas) pra atacar o gargalo de captação de alunos e
credibilidade na cidade.

**Estrutura de pastas:**
- `_memoria/` — quem é a Move, como ela fala, foco atual
- `identidade/` — marca aplicada em tudo que o sistema gera (logo, fotos da estrutura, cores)
- `marketing/` — conteúdo, SEO e campanhas (`conteudo/`, `seo/`, `campanhas/`, `avaliacoes-google/`)
- `dados/` — drop zone de arquivos de entrada (CSV, planilhas, PDFs) pra skills lerem
- `saidas/` — outputs pontuais que não são de marketing (análises, emails, relatórios diversos)
- `scripts/` — utilitários que as skills chamam (geração de imagem, publicação em rede social, render de HTML)
- `site/` — site institucional (Astro, repositório git próprio, deploy na Vercel). Ver seção "Site da Move" abaixo
- `templates/` — modelos reaproveitáveis (skills, identidade, ferramentas)

## Sobre a empresa

Move Academia Personalizada é uma academia em Medianeira/PR (Av.
Brasília, 2211, Cidade Alta). Atua em treinamento personalizado e
coletivo — musculação, funcional, fichas de treino, avaliação física
e fisioterapia pélvica (diferencial de nicho) — atendendo público
adulto da cidade e região, com forte apelo a mulheres interessadas em
saúde pélvica. Equipe ainda não mapeada em detalhe (ver
`_memoria/empresa.md`).

## O que mais fazemos aqui

- Posts institucionais (planos, horários, regras)
- Posts de bastidores/comunidade (alunos, conquistas, humor de Reels)
- Conteúdo sobre fisioterapia pélvica e diferenciais técnicos
- Campanhas de captação de novos alunos

## Tom de voz

Caloroso e comunitário, com orgulho de conquistas dos alunos. Direto
e informativo em conteúdo institucional. Descontraído/humor em
bastidores e Reels. Ver `_memoria/preferencias.md` pro exemplo real e
lista completa do que evitar (nada de "vamos juntos!", emoji forçado,
"caro cliente", jargão de guru).

## Regras do sistema

- Conteúdo (posts, carrosséis) é a prioridade nº 1 — é a tarefa que
  mais pesa no dia a dia da Move
- Conteúdo de marketing (posts, SEO, campanhas) salva em `marketing/`
- Análises, emails e relatórios pontuais salvam em `saidas/`
- Toda peça visual deve seguir `identidade/design-guide.md`
- **Push automático:** ao terminar uma edição de arquivo, comitar e dar
  push sozinho, sem perguntar, no repositório correto (o do `site/` quando
  a edição for no site; o do workspace nos demais casos). Só avisar depois.

## Site da Move

- `site/` é um projeto Astro com repositório git **próprio**, ignorado pelo
  git do workspace. Remoto: `https://github.com/Neresb/Move-Heckos` (privado).
  Deploy na Vercel: push na `main` publica automaticamente
- Blog: artigos em `site/src/content/blog/<slug>.md` com frontmatter
  (`title`, `description`, `publishedAt`, `author`, `keywords`, `draft`) —
  é o destino da skill `/publicar-tema`. Post só aparece com `draft: false`
- PNGs de carrossel publicados vão em `site/public/` (fluxo `/aprovar-post`)
- Dados oficiais do negócio no site (planos, preços, horários, WhatsApp)
  ficam centralizados em `site/src/consts.ts` — editar lá, não nas páginas
- Domínio: subdomínio Vercel por enquanto. Quando tiver domínio final,
  atualizar `site` em `site/astro.config.mjs` e o sitemap em
  `site/public/robots.txt`

## Ferramentas conectadas

- [ ] Notion
- [ ] Gmail
- [ ] Google Calendar
- [ ] Google Ads
- [ ] Meta Ads
- [ ] Slack

*(Marcar conforme for instalando os MCPs)*

---

# HeckOS — Sistema operacional do negócio

Sua empresa roda em cima desse arquivo. Aqui ficam as regras de operação
do HeckOS — como o Claude lê o contexto, aprende com correções, mantém
tudo atualizado e cria skills novas conforme a operação evolui.

Esse arquivo é editável. Quando o `/instalar` rodar, ele complementa o
final dessa página com as regras específicas do seu negócio.

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (quando existirem
e estiverem preenchidos):

1. `_memoria/empresa.md` — quem é o usuário, o que faz, como funciona o negócio
2. `_memoria/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_memoria/estrategia.md` — foco atual, prioridades, prazos

Usar essas informações como base pra qualquer resposta ou decisão. Ao
sugerir prioridades, formatos ou abordagens, considerar o foco atual
descrito em `estrategia.md`.

Pra qualquer tarefa visual (carrossel, post, landing page), consultar
`identidade/design-guide.md` como referência de estilo.

Não é necessário listar o que foi lido nem confirmar a leitura. Apenas
usar o contexto naturalmente.

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe skill relevante
em `.claude/skills/`. Se encontrar, seguir as instruções da skill. Se
não encontrar, executar a tarefa normalmente.

Ao concluir uma tarefa que não tinha skill mas parece repetível (o
usuário provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

Não perguntar pra tarefas pontuais ou perguntas simples. Só quando o
padrão de repetição for claro.

---

## Aprender com correções

Quando o usuário corrigir algo, melhorar uma resposta ou dar uma
instrução que parece permanente (frases como "na verdade é assim", "não
faça mais isso", "prefiro assim", "sempre que...", "evita...", "da
próxima vez..."), perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negócio** (clientes, serviços, mercado) → `_memoria/empresa.md`
- **Sobre preferências e estilo** (tom de voz, formato, o que evitar) → `_memoria/preferencias.md`
- **Sobre prioridades e foco** (projetos, metas, prazos) → `_memoria/estrategia.md`
- **Regra de comportamento nessa pasta** → próprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro.
Confirmar mostrando a linha adicionada.

Não perguntar se a correção for óbvia de contexto imediato (ex: "na
verdade o arquivo se chama X"). Só perguntar quando a informação tiver
valor duradouro.

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante (cliente novo, skill
nova, mudança de foco, processo novo, ferramenta instalada, estrutura
alterada), perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize a memória?"

Se sim, identificar o que atualizar:

- **Cliente, serviço, ferramenta, equipe** → `_memoria/empresa.md`
- **Mudança de prioridade ou foco** → `_memoria/estrategia.md`
- **Tom ou estilo** → `_memoria/preferencias.md`
- **Pasta, regra de organização, skill criada** → `CLAUDE.md`
- **Visual (cores, fontes, logo)** → `identidade/design-guide.md`

Mostrar o que vai mudar antes de salvar. Não reformatar o arquivo
inteiro, só adicionar ou editar a linha relevante.

**Quando NÃO perguntar:**
- Tarefas pontuais sem impacto no contexto (escrever um email avulso, criar um post)
- Perguntas simples ou conversas sem ação
- Mudanças já salvas pelo bloco "Aprender com correções"

**Dica:** rode `/atualizar` pra uma varredura completa quando houver dúvida.

---

## Criação de skills

Quando o usuário pedir skill nova:

1. Verificar se existe template relevante em `templates/skills/`. Se
   existir, usar como base e adaptar pro contexto
2. Perguntar se é específica desse projeto ou útil em qualquer:
   - Específica → `.claude/skills/nome-da-skill/SKILL.md` (local)
   - Universal → `~/.claude/skills/nome-da-skill/SKILL.md` (global)
3. Ler `_memoria/empresa.md` e `_memoria/preferencias.md` pra calibrar
   o conteúdo da skill ao contexto do negócio
4. Se a skill precisar de arquivos de apoio (templates, exemplos),
   criar dentro da pasta da skill
5. Seguir o fluxo da skill-creator nativa do Claude Code
