# AGENTS.md

## Diretrizes do agente

> Contrato operacional, válido para qualquer tarefa neste repositório. As seções seguintes explicam o *porquê* e o *como*; esta é o que **não muda**. Se uma instrução da conversa conflitar com estas diretrizes, perguntar antes de agir.

### Papel

Trabalhar a **vitrine pessoal** do dono do perfil: `README.md` (portfólio no GitHub) e `index.html` (currículo no GitHub Pages). Não há código-fonte, framework nem build — a manutenção é de **conteúdo, layout e consistência entre os dois documentos**. O `README.md` é a fonte da verdade; o currículo deriva dele.

### Antes de mexer em qualquer coisa

1. `git status`, `git diff`, `git log --oneline -10` — o dono pode ter editado no meio da sessão (ver "Separar mudanças misturadas").
2. Ler o trecho alvo nos **dois** arquivos (`README.md` e `index.html`): quase toda informação existe nos dois lados.
3. Conferir os números vigentes: `101` projetos, `44` catalogados, `33` certificações, `1130h` (653h + 477h), `87` elementos com `data-en`.
4. `/tmp/opencode/` nasce vazio a cada reinício: os scripts de validação e o `jsdom` precisam ser recriados/reinstalados na sessão (ver "Validação como CI").

### Regras inegociáveis

- **README manda.** Nenhum dado entra no currículo que não exista na linha correspondente do README; divergência entre os dois é o defeito mais provável do repositório.
- **Texto novo no currículo sempre nas DUAS versões** (pt-BR + `data-en`), na mesma edição. `data-en` substitui o `innerHTML` inteiro, é HTML escapado (`html.escape(en, quote=True)`), nunca vazio e nunca com `<` cru.
- **Nenhum número novo num arquivo sem atualizar o equivalente no outro** (101, 44, 33, 1130h, 653h, 477h).
- **Documento estático:** não introduzir `package.json`, framework, CDN, build ou toolchain no repositório. JavaScript no máximo o seletor de idioma que já existe.
- **HTML balanceado** nos dois arquivos (`html.parser` do Python, não `xmllint`); `<title>` sempre presente; ids de `<details>` únicos.
- **Commit no fim de cada tarefa, sempre** (ordem do dono: "sempre faça commit no final"): um assunto por commit, mensagem em pt-BR no formato `tipo: descrição`, nunca `rebase`/`amend`/`reset`. Antes de commitar: `git status`, `git diff`, `git log --oneline -10`.
- **Nada versionado fora do combinado:** scripts e venvs ficam em `/tmp/opencode/`, nunca no repositório; certificados são só os `.jpg` (sem `UC-...`).
- **Modelo não lê imagem:** texto de certificado sai por OCR (seção "Como extrair os nomes dos cursos"), nunca pedindo ao dono para redigitar.

### Fluxo de uma tarefa

1. **Analisar** (comandos acima) e localizar os dois pontos de edição.
2. **Editar** os dois lados; se for texto do currículo, PT e `data-en` juntos.
3. **Validar** antes de dizer pronto: bloco "Validação obrigatória" + "Como validar as duas versões".
4. **Registrar** em "Registro de conceitos e ideias" (o *porquê* de decisões e armadilhas) e em "Histórico do trabalho" (o *que foi feito*).
5. **Commitar** no fim de cada tarefa, um assunto por vez (ver "Regras inegociáveis").

### Ao encerrar

Revisar as seções de registro do `AGENTS.md`: conceito novo que não entrou e histórico desatualizado são falhas da tarefa, mesmo com o conteúdo certo. Este arquivo é a memória entre sessões — nada pode depender do contexto da conversa.

## Contexto do projeto

Repositório de perfil do GitHub **DaFi-1/DaFi-1**. Não contém código-fonte; é uma vitrine pessoal formada por dois arquivos e uma pasta de imagens:

- **`index.html`** — Currículo (estilo Lattes) do dono do perfil. Conteúdo em português (pt-BR), single-file com CSS inline e ícones SVG embutidos. Estrutura em seções numeradas (1. Contato → 9. Idiomas). A seção 5 (Certificações) tem `id="certifications"`, usado como âncora pelo link do README.
- **`README.md`** — Apresentação do perfil no GitHub (profile README), exibida na página principal do usuário. É o catálogo de projetos e habilidades, organizado em abas `<details>`/`<summary>` (Skills, Ebooks, Certifications, Social impact, Framework, Cybersecurity, DevOps, Backend, Systems, FrontEnd, GameDev, Deep Learning, Testing, NeoVim, Forks, Trash, Gaming-Diary). Rótulos em inglês; conteúdo e imagens em pt-BR, **exceto os títulos das certificações, que são em inglês**.
- **`certification/`** — Imagens dos certificados, organizadas por ano em `certification/<ano>/cerification-<n>-<h>h-(<ano>).jpg`. São 33 imagens: 18 em `2023/` e 15 em `2024/`.

## Conceito do trabalho

O repositório é a **vitrine pessoal** de um desenvolvedor full-stack brasileiro, em dois formatos que se complementam: um **portfólio** (`README.md`, a página do perfil no GitHub) e um **currículo** (`index.html`, publicado no GitHub Pages, estilo Lattes). Nenhum código-fonte: a manutenção é de conteúdo, layout e consistência.

Cinco conceitos sustentam o trabalho. Qualquer ideia nova precisa se encaixar em um deles ou explicar por que não:

1. **Fonte única de verdade.** O README manda. Os números (`101` projetos, `44` catalogados, `33` certificações, `1130h`) e o conteúdo das seções 4 e 6 do currículo derivam dele. O defeito mais provável do repositório é a divergência entre os dois documentos, então toda alteração é conferida nos dois lados.
2. **Documento estático, sem build.** Um arquivo só, CSS inline, ícones SVG embutidos, sem framework, sem `package.json`, sem CDN. O único JavaScript é o seletor de idioma no fim do `<body>`. Site novo não justifica introduzir toolchain.
3. **Bilinguismo por atributo.** O português é a fonte da verdade (aparece sem JS e para os buscadores) e o inglês vive em `data-en`. Isso torna a tradução um contrato de par de arquivos dentro do mesmo HTML, e obriga a editar os dois lados juntos.
4. **Validação como CI.** Não existe lint, build nem teste no repositório, então a checagem é feita por scripts em `/tmp/opencode/` (validador de certificações e testes com `jsdom`) e por conferência visual. Se um número aparece no site, existe um script que o confere.
5. **Memória no `AGENTS.md`.** O arquivo é a memória do projeto entre sessões: o agente não deve depender de contexto de conversa. Daí a regra de registrar conceitos novos abaixo.

## Registro de conceitos e ideias

> **Regra: qualquer conceito novo, ideia, decisão de design ou armadilha descoberta entra neste `AGENTS.md`, com o contexto suficiente para outra IA (ou para o dono, daqui a seis meses) entender o porquê sem precisar perguntar.** Não basta descrever *o que* foi feito: registre *por que*, *como*, *onde no código* e *o que já quebrou*. Se a ideia veio de um pedido do dono, cite o pedido. Se afetou os dois documentos, diga como manter os dois em sincronia. Ao encerrar uma tarefa, revisar esta seção e a de "Histórico do trabalho".

Formato de cada entrada (copiar e preencher):

```markdown
### <nome do conceito> — <data>
- **O que é:** ...
- **Por que existe:** ... (problema que resolve)
- **Como funciona:** ... (mecânica, arquivos envolvidos)
- **Onde está:** ... (arquivo:linha, seção do HTML, id)
- **Armadilha:** ... (o que já deu errado)
```

Conceitos já registrados:

### Fonte única de verdade (README → currículo) — 2026-09-25
- **O que é:** toda ONG, projeto, link, status e stack do currículo vem da linha correspondente do README.
- **Por que existe:** os dois documentos descrevem a mesma pessoa; sem regra, eles divergem silenciosamente (já houve: nome do projeto Docker diferente, links de ONG com typo, status divergente).
- **Como funciona:** a linha do README é a fonte; o currículo reescreve o mesmo dado como frase curta. Alteração no currículo ⇒ conferir o README antes; alteração no README ⇒ revisar o currículo.
- **Onde está:** aba Social impact do README ↔ seção 4 do currículo; abas de projeto ↔ seção 6; Skills ↔ seção 7.
- **Armadilha:** a seção 6 do currículo lista só o que tem repositório público, então itens "Em breve" do README não aparecem lá — não é divergência.

### Certificações pelo pipeline OCR — 2026-09-25
- **O que é:** os nomes dos 33 cursos vieram de OCR das imagens, não de digitação.
- **Por que existe:** o modelo não consegue ler imagens e o dono não deve redigitar o que já está nas imagens.
- **Como funciona:** venv temporário com `rapidocr-onnxruntime` → `RapidOCR()` por imagem, título na faixa de 30%–62% da altura (layout Udemy), correção manual de acentos, gravação nos dois arquivos.
- **Onde está:** seção "Como extrair os nomes dos cursos (OCR)".
- **Armadilha:** OCR perde acentos e troca caracteres (`API`→`APl`, `&`→`e`, `SQLAlchemy`→`SQL Alchemy`); o venv pesa 392 MB em `/tmp` e precisa ser removido.

### Validação como CI — 2026-09-25
- **O que é:** scripts em `/tmp/opencode` no lugar de pipeline de teste.
- **Por que existe:** o repositório não tem `package.json`, `Makefile` nem CI, e os números do site (contadores, horas, links) quebram silenciosamente.
- **Como funciona:** `validate_certs.py` confere nomes, ordem, somas e links nos dois arquivos; `test_lang.js` e `test_certs_en.js` (jsdom) carregam a página e clicam em PT/EN conferindo textos, links, ícones, `title` e `meta`; `node --check` valida o script do currículo.
- **Onde está:** seção "Validação obrigatória" e "Como validar as duas versões".
- **Armadilha:** `/tmp` é RAM e some a cada reinício; se `jsdom` faltar, reinstalar com `cd /tmp/opencode && npm install jsdom`. Os scripts vivem fora do repositório de propósito.

### Commits atômicos e descritivos — 2026-09-25
- **O que é:** um assunto por commit, mensagens curtas em pt-BR no formato `tipo: descrição`.
- **Por que existe:** o histórico tem 326 commits com a mesma mensagem `Up`, o que torna impossível saber o que mudou e o porquê.
- **Como funciona:** commits separados por assunto (imagens / currículo / documentação), nunca misturar `docs` com conteúdo nem imagens com texto.
- **Onde está:** seção "Fluxo de trabalho e commits".
- **Armadilha:** misturar assuntos num commit só; ver também "Commit no fim de cada tarefa" (regra vigente desde 2026-09-26).

### Separar mudanças misturadas sem reescrever histórico — 2026-09-25
- **O que é:** quando o dono edita um arquivo no mesmo working tree em que o agente já travaille, os dois conjuntos de mudanças ficam no mesmo `git diff` e viram um commit só. A técnica isola os dois sem reescrever histórico, usando cópias em `/tmp/opencode` como palco.
- **Por que existe:** no pedido de "vários commits", o dono já tinha editado o `README.md` (capa comentada, cabeçalho sem `44`, `<summary>` com link) **e** o agente tinha corrigido 2 ONGs no mesmo arquivo. Commitar tudo junto violaria "um assunto por commit" e atribuiria ao dono mudanças que ele não fez.
- **Como funciona:** (1) `cp README.md /tmp/opencode/readme.final.md` guarda o estado final com as duas coisas; (2) um script reverte **apenas as linhas do agente**, deixando o `git diff` com só o que é do dono; (3) `git add` + `git commit` do ajuste dele; (4) `cp /tmp/opencode/<arquivo>.final.md <arquivo>` restaura o estado completo, de modo que a próxima emenda seja só a correção do agente. O mesmo caminho foi usado em `index.html` com `/tmp/opencode/index.final.html` (com o fix das ONGs) e `/tmp/opencode/index.sem_fix.html` (bilingue, sem o fix). Conferir com `git diff -U0 | grep -E '^[+-][^+-]'` antes de cada `git add`.
- **Onde está:** commits `a842531` (ajuste do dono), `b9b203a` (bilinguismo, sem o fix), `83aff60` (fix das ONGs no README e no currículo). Nenhum `git rebase`, `commit --amend` ou `reset` foi usado.
- **Armadilha:** a ordem importa — commitar o ajuste do dono **primeiro**, senão o fix do agente entra junto. E o arquivo em `/tmp` precisa existir antes de começar, porque `/tmp` é tmpfs e some a cada reinício.

### Títulos de certificação em inglês no README — 2026-09-26
- **O que é:** os 28 títulos traduzidos da aba Certifications do `README.md` foram trocados do português para o inglês — exatamente o texto do `data-en` do currículo. As 5 que já eram em inglês não mudaram. As 33 linhas continuam com mesmo `href`, mesmas horas e mesma ordem.
- **Por que existe:** pedido do dono ao colar a aba inteira: "veja os nomes em inglês no site index.html e coloque em inglês aqui no readme, não precisa deixar em português". O README tem rótulos em inglês e o público dele é internacional; o currículo continua com português como conteúdo padrão.
- **Como funciona:** fonte do texto é o `data-en` da seção 5 do currículo (o par `href` → título em inglês). Troca só o texto do `<a>`, nunca o `href` nem as células de horas/ano.
- **Onde está:** `README.md`, aba Certifications (linhas de `certification/2023/...` e `certification/2024/...`).
- **Armadilha:** a inversão é só aqui — nestas 33 linhas o inglês vem do currículo e o português fica no currículo; os demais dados continuam vindo do README. Se um título for re-traduzido, trocar nos dois ao mesmo tempo. `&` precisa de `&amp;` no README (`The Git &amp; Github Bootcamp`).

### Commit no fim de cada tarefa — 2026-09-26
- **O que é:** toda tarefa termina com commit, sem esperar pedido específico para cada uma.
- **Por que existe:** pedido do dono ("sempre faça commit no final"). Substitui a regra antiga de "não commitar sem pedido explícito": o pedido agora é permanente e vale por padrão.
- **Como funciona:** ao fim do fluxo (após validar e registrar no `AGENTS.md`), fazer `git status` → `git diff` → `git log --oneline -10` e commitar um assunto por vez, mensagens em pt-BR no formato `tipo: descrição`. Mudanças de conteúdo e de documentação em commits separados.
- **Onde está:** "Regras inegociáveis" e "Fluxo de trabalho e commits".
- **Armadilha:** não misturar assuntos num commit só só porque a tarefa foi rápida; e nunca `rebase`, `amend` ou `reset` para "arrumar" o que já foi commitado.

## Os dois documentos e como eles se relacionam

Os dois arquivos descrevem a **mesma pessoa e o mesmo trabalho**, mas para públicos diferentes. Nenhum é cópia do outro: a mesma informação aparece nos dois com layout, granularidade e ênfase diferentes, e nenhum dos dois pode contradizer o outro.

| Aspecto | `README.md` (perfil do GitHub) | `index.html` (currículo Lattes) |
| --- | --- | --- |
| Onde fica | `github.com/DaFi-1` (profile README) | `https://dafi-1.github.io/DaFi-1/` (GitHub Pages) |
| Leitor | Visitantes, recrutadores técnicos, quem avalia o portfólio | Recrutadores, pesquisadores CNPq e empregadores |
| Finalidade | Catálogo do que **existe**: 101 projetos, 44 catalogados, 33 certificações, forks, ebooks, lixo | Documento formal, curto e sequencial, para ser lido do começo ao fim |
| Estrutura | Uma linha de contadores + 17 abas `<details>` recolhíveis | 9 seções numeradas, sempre abertas |
| Seções | 1 Skills, 2 Ebooks, 3 Certifications, 4 Social impact, 5 Framework, 6 Cybersecurity, 7 DevOps, 8 Backend, 9 systems, 10 FrontEnd, 11 GameDev, 12 Deep Learning, 13 Testing, 14 NeoVim, 15 Forks, 16 Trash, 17 Gaming-Diary | 1 Contato, 2 Resumo, 3 Experiência Profissional Freelance, 4 Contribuições para ONGs, 5 Certificações, 6 Projetos Pessoais, 7 Stacks, 8 Formação Acadêmica, 9 Idiomas |
| Idioma dos rótulos | Inglês: `Skill`, `Course`, `Hours`, `Year`, `Stack`, `Completed` | Português: `Contato`, `Resumo`, `Certificações`, `Stacks` |
| Texto do conteúdo | Nome do repositório, badges de stack, um emoji de status | Frases completas dizendo o que foi feito, com `<p class="title">` e listas com marcadores |
| Contadores | `101` projetos e `33` certificações - `1130h` no cabeçalho; `44` catalogados na soma das abas | `Total de projetos: 101 projetos.` e `Total: 33 certificações - 1130h.` |
| Contato | Só um link para o currículo no cabeçalho | GitHub, Lattes (`lattes.cnpq.br`) e e-mail completos |

### O que existe em cada um

- **Só no README:** a aba Skills (badges do shields.io por área), as 15 abas de projetos (Ebooks, Social impact, Framework, Cybersecurity, DevOps, Backend, systems, FrontEnd, GameDev, Deep Learning, Testing, NeoVim, Forks, Trash, Gaming-Diary), os badges `+10` de dificuldade, a imagem de capa e o bloco `<h3>` antigo comentado.
- **Só no currículo:** Contato, Resumo, a Experiência Freelance com as 4 empresas (Tech Leader, JapanGames, ONGs, InGames), Stacks, Formação Acadêmica e Idiomas com nível.
- **Nos dois:** os projetos pessoais e as 33 certificações. Os 8 projetos da seção 6 do currículo (`nmget`, `fiwm`, `lattes-html-sanitization`, `10-Docker-Project`, `100-Html-Css-Js-Project`, `100-Pytest-Projects`, `PerceptronGuide`, `tasknvim`) aparecem no README dentro de abas diferentes, conforme a categoria de cada um.

### Ligações entre os documentos

- O único link direto entre eles é o cabeçalho do README: `📄 Currículo` → `https://dafi-1.github.io/DaFi-1/`. O currículo não aponta de volta para o README.
- Ambos abrem repositórios no mesmo endereço: `https://github.com/DaFi-1/<repo>`. Projeto sem repositório público usa `https://github.com/DaFi-1` com `title="Em breve"`.
- Ambos abrem a mesma imagem de certificado: `certification/<ano>/cerification-<n>-<h>h-(<ano>).jpg`. A seção 5 do currículo tem `id="certifications"` para permitir links diretos a ela.
- O currículo e o README descrevem as mesmas ONGs: no currículo são frases dentro das seções 3 e 4; no README são linhas da aba Social impact (`ONGs-*-site` e `ONGs-*-software`).

### Mesma informação, formatos diferentes

| Informação | No README | No currículo |
| --- | --- | --- |
| Projeto pessoal | Linha de tabela: `1` | nome do repo, link, marcador de concluído e descrição em uma frase |
| Projeto pessoal (sem repo) | `ONGs-ongab-site` marcado como `❌ In Development` | Não entra na seção 6 (que lista só o que tem link público) |
| Stack | Coluna `Stack` com texto (`Docker`) ou badges na aba Skills | Seção 7, agrupada por área (`Backend: Python, Django, Flask e FastAPI`) |
| Status | Coluna sem título com `✅` ou `❌`, legenda `✅ Completed \| ❌ In Development` | Texto `(concluído).` ou `(em desenvolvimento).` dentro de `<span class="period">` |
| Certificação | Linha com `Course` (link, **título em inglês**), `Hours` (`131h`) e `Year` (`2023`) | `Nome do curso (2023). 131h.` com o nome linkado (título em português, inglês no `data-en`) |
| Total | Só nos contadores do cabeçalho e do `<summary>` da aba | Frase `Total: ...` no topo da seção, antes dos tópicos |
| Experiência | Não existe | Seção 3, uma entrada por empresa, com o tipo de contrato na segunda linha |

### Regras de sincronia

- **O `README.md` é a fonte da verdade.** O `index.html` não inventa dados: toda ONG, projeto, link, status e stack da seção 4 e da seção 6 sai do README (aba correspondente) e é reescrito em frase curta para o currículo. Ao atualizar um projeto no currículo, conferir primeiro a linha correspondente no README; ao atualizar no README, revisar o currículo.
- **Projeto novo:** escolher a aba correspondente no README, inserir a linha numerada, renumerar as linhas seguintes da mesma aba, atualizar o contador do `<summary>` da aba e, se a soma mudar, revisar o número de projetos do cabeçalho. Se for projeto pessoal de destaque, avaliar incluir na seção 6 do currículo.
- **Certificação nova:** jpg em `certification/<ano>/`, uma linha na tabela do ano correspondente no README e um item na seção 5 do currículo, mantendo a ordem decrescente de horas. Atualizar o subtítulo do ano, o `<summary>`, o cabeçalho e a linha de total do currículo. O texto do link no README é o **título em inglês**; o título em português vive só no currículo (ver "Títulos de certificação em inglês no README").
- **Repo renomeado ou apagado:** atualizar os dois arquivos, verificando se o nome também aparece em `<b>` no currículo e no `title` dos links do README.
- **Nova skill/tech:** entra nos dois (badges na aba Skills e item na seção 7 do currículo), com o mesmo nome de tecnologia.
- **Nunca** introducir um número em um arquivo sem atualizar o número equivalente no outro (101, 44, 33, 1130h, 653h, 477h).
- **Conceito novo ou ideia nova** vai para "Registro de conceitos e ideias", e o que foi feito para "Histórico do trabalho". Não encerrar tarefa sem revisar as duas seções.

## Idiomas do currículo (`index.html`)

> **Regra principal: toda alteração de texto no currículo é feita nas DUAS versões, pt-BR e EN, na mesma edição.** Nunca deixar texto novo só em português. Se o texto é idêntico nos dois idiomas (nome de empresa, tecnologia, `GitHub:`, horas, ano), não cria `data-en`. Antes de dar qualquer coisa por pronta, conferir a versão EN rodando os testes desta seção.

O currículo é bilíngue (pt-BR / EN), implementado sem framework e sem build:

- O texto em português é o conteúdo do HTML (fonte da verdade, aparece sem JS e nos buscadores). A versão inglesa fica no atributo `data-en` de cada elemento traduzível.
- O script no fim do `<body>` troca `el.innerHTML` entre o valor salvo na página (PT) e `data-en` (EN), atualiza `<title>`, a `<meta description>` e o atributo `lang` do `<html>`, marca o botão ativo com `aria-pressed` e guarda a preferência em `localStorage["cv-lang"]`. Sem JS, o site aparece em português.
- **O `data-en` substitui o `innerHTML` inteiro do elemento.** Ao traduzir, é obrigatório incluir todo o conteúdo: rótulo **e** valores, links, `<b>`, `<span class="period">` e o ícone SVG. Um `data-en='<b>Languages:</b>'` sem a lista de tecnologias apaga a lista ao trocar de idioma (erro que já aconteceu).
- O conteúdo do `data-en` é HTML **escapado** (`&lt;b&gt;`, `&quot;`), gravado com `html.escape(en, quote=True)`. Nunca escrever `<` ou `>` crus dentro do atributo: quebra o balanceamento do `html.parser` e a validação.
- **Os títulos das 33 certificações são traduzidos** no currículo (`data-en` na seção 5), apontando para a **mesma** imagem `.jpg`, com o mesmo `(ano). NNh.`. Os 5 títulos que já estavam em inglês (`Complete SQL and Databases Bootcamp`, `Django - The Python Practical Guide`, `The Git & Github Bootcamp`, `SQLite Databases Python Programming`, `Intro To SQLite Databases Programming`) ficam sem `data-en`. O `README.md` **não** é bilíngue: as tabelas dele usam o título **em inglês** (o mesmo `data-en` do currículo) e o currículo mantém o português como conteúdo padrão (ver "Títulos de certificação em inglês no README").
- Não se traduzem: nomes próprios (empresas, ONGs, repositórios), tecnologias, horas, anos, e-mail e URLs. Rótulos idênticos nos dois idiomas (`GitHub:`, `E-mail:`, `Frontend:`, `Backend:`, `Machine learning:`, `Data science:`, `DevOps:`, nomes das 4 empresas) ficam sem `data-en`.
- Para adicionar um trecho novo: criar o elemento em PT, duplicar o inner HTML em inglês com o helper `d()` do script `/tmp/opencode/add_i18n.py` (que aplica tudo com asserções e é reexecutável a partir do backup), e conferir com o teste jsdom. Para certificações novas, o dicionário PT→EN está em `/tmp/opencode/add_i18n_certs.py`.

### O que já foi feito (histórico do bilinguismo)

1. **Botão PT/EN** no topo da página (`.lang-switch`, dois `<button data-lang>`, `aria-pressed`), com a preferência em `localStorage["cv-lang"]`. Padrão de estilo em `index.html` (`for-the-badge` não se aplica aqui: é HTML puro, badges só no README).
2. **59 elementos traduzidos** na primeira leva: 9 títulos de seção, resumo, as 4 entradas de experiência (título, subtipo e 13 frases), 9 itens de ONGs, os dois totais (certificações e projetos), 8 projetos pessoais, Stacks, formação e idiomas.
3. **28 títulos de certificação traduzidos**, cada linha com o mesmo `href` de imagem, mesmo `(ano). NNh.` e mesma ordem. Os 5 títulos que já estavam em inglês ficaram sem `data-en`.
4. **`<meta description>` e `<title>` bilíngues**: o script troca `content` na `<meta>` e o texto do `<title>`, além do `lang` do `<html>`.
5. **Limpeza na seção 6**: o marcador `(concluído).` foi removido dos 7 projetos concluídos (em PT e no `data-en`); só o `100-Html-Css-Js-Project` mantém `(em desenvolvimento).` / `(in development).`. Regra: status só quando o projeto **não** está pronto.
6. Estado atual: **87 elementos com `data-en`** (59 + 28).

### Erros já encontrados (não repetir)

- `data-en` só com o rótulo, sem os valores → os valores somem ao trocar de idioma (aconteceu nas linhas de Stacks).
- `data-en` com `<b>`/`<a>` crus → o `html.parser` acusa HTML desbalanceado e a validação quebra. Sempre `html.escape(en, quote=True)`.
- Regex do validador de certificações contava as cópias em inglês como linhas duplicadas. Ele agora remove os `data-en` antes de contar (`index_pt` em `/tmp/opencode/validate_certs.py`).
- Um `data-en=""` apaga o elemento ao trocar de idioma. Nunca deixar atributo vazio.

### Como validar as duas versões

```bash
python3 - <<'PY'
import re; s=open("/home/a/DaFi-1/index.html",encoding="utf-8").read()
open("/tmp/opencode/cv.js","w").write(re.search(r'<script>(.*?)</script>',s,re.S).group(1))
PY
node --check /tmp/opencode/cv.js        # sintaxe do script
node /tmp/opencode/test_lang.js         # troca PT/EN: textos, links, ícones, title, meta, aria-pressed
node /tmp/opencode/test_certs_en.js     # 33 certificações: PT x EN, mesmo href/ano/horas
python3 /tmp/opencode/validate_certs.py # nomes, ordem, somas e links nos dois arquivos
```

O `test_lang.js` termina com a guarda que impede o erro mais comum: acusa qualquer `[data-en]` que perca texto na troca (`elementos que perderam texto: 0`). O único "vazio" aceitável é a `<meta>`, que não tem texto. Se `jsdom` não estiver instalado em `/tmp/opencode/node_modules`, rodar `cd /tmp/opencode && npm install jsdom` (precisa de internet).

## Convenções

- Idioma dos arquivos: **português (pt-BR)**. Comentários/código em inglês quando técnico.
- Links de repositórios apontam para `github.com/DaFi-1/<repo>`.
- Projetos sem repositório publicado usam `https://github.com/DaFi-1` como destino (título "Em breve").
- Estado dos projetos: `✅` concluído | `❌` em desenvolvimento.
- `<details>`: cada aba precisa de `id` **único** e contagem de projetos consistente com o número de linhas da tabela.
- Separadores em números de resumo usam **hífen simples** com espaços (`2023 - 18 certifications - 653h`), nunca travessão.

## Regras

- Sempre manter os contadores do README (header, títulos das abas) consistentes entre si e com o que está listado.
- Manter `index.html` e `README.md` alinhados: mesmos arquivos de certificado, mesma ordem, mesmas horas e mesmo ano.
- Alterações em `index.html` devem preservar HTML balanceado (todas as tags abertas foram fechadas) e incluir `<title>`.

## Formato da aba Certifications

As duas entradas (README e currículo) seguem exatamente o mesmo formato:

- Uma linha por imagem, ordenada da **maior para a menor** carga horária dentro de cada ano.
- Dois tópicos, `2023` e `2024`, nessa ordem, com subtítulo no formato `ano - quantidade - horas`.
- Colunas no README: `Course | Hours | Year`. No currículo: `Nome do curso (ano). 131h.` com o nome linkado para a imagem.
- O nome do curso é o **texto do link** que aponta para o `.jpg`; não existe coluna com "Certificação 01". No README esse texto é o título em inglês; no currículo é o título em português com o inglês no `data-en`. Os dois apontam para o mesmo arquivo e são a mesma tradução.
- Contador no `<summary>` do README: `(33 certifications - 1130h)`. No cabeçalho do README: `🎓 Certifications - 33 - 1130h`.
- No currículo, a linha `Total: 33 certificações - 1130h.` fica no **topo** da seção 5, antes dos tópicos. Ela **não** existe no README.
- Somas atuais: 2023 = 653h (18 cursos), 2024 = 477h (15 cursos), total = 1130h.
- As horas dos arquivos são arredondadas para cima. A soma exata impressa nos certificados é 1120h (647,5h + 472,5h). Hoje valem os valores das tabelas (1130h); se trocar, atualizar tabelas, subtítulos e cabeçalho juntos.

## Ambiente e limitações conhecidas

- **O modelo não consegue ler imagens.** Para extrair texto dos certificados é obrigatório usar OCR (ver seção seguinte). Não pedir ao usuário para digitar nomes que já estão nas imagens.
- Não há `sudo`, `apt`, `tesseract`, `exiftool`, `Pillow` nem `xmllint` útil. Só existe `python3` (3.14) e `node`. Há internet e `pip` funciona.
- `/tmp` é tmpfs (RAM). O ambiente virtual de OCR ocupa ~392 MB: criar, usar e **remover** ao terminar.
- `multiprocessing` com o contexto padrão (`forkserver`) falha neste ambiente; usar `mp.get_context("fork")` ou `maxtasksperchild`/sequencial.
- `xmllint --html` accuse `svg`, `section`, `symbol`, `use`, `path` como tags inválidas: são falsos positivos do parser HTML4 do libxml2. Para balanceamento, usar `html.parser` do Python.

## Como extrair os nomes dos cursos (OCR)

Receita usada com sucesso, tudo fora do repositório:

```bash
python3 -m venv /tmp/opencode/ocr
/tmp/opencode/ocr/bin/pip install rapidocr-onnxruntime   # ~392 MB, modelos embutidos
```

Depois, um script que chama `RapidOCR()` para cada `.jpg`, com `Pool(4, initializer=init, mp_context=mp.get_context("fork"))`, e grava por imagem: altura, posição, score e texto. Os JPEGs não têm metadados (`strings` não retorna nada de útil).

Como extrair o título de cada certificado (layout da Udemy, 1600×1190):

- O título é a linha mais alta da faixa entre ~30% e ~62% da altura da imagem; normalmente são 2 a 3 linhas de texto grandes.
- Ignorar: `Udemy`/`udemy`/`tdemy` (logo), `CERTIFICADO DE CONCLUSÃO`, `Instrutores ...`, o nome do aluno, `Data ...`, `Duracao ...`, `N do certificado`, `URL do certificado`, `Numero de referencia`.
- O OCR **perde acentos** ("Programacao", "Alchemy", "SQLAlchemy" → "SQL Alchemy", `API` → `APl`, `&` → `e`). Corrigir manualmente ao escrever nos arquivos.
- Cada certificado tem um identificador `UC-...` e a URL `ude.my/UC-...`; não versionar esses dados, apenas a imagem.

Validação usada na época: 33 linhas, soma 1130h, HTML balanceado e nomes conferidos contra o OCR. Essas checagens devem ser repetidas como descrito em "Validação obrigatória".

## Validação obrigatória

Não existe lint, build, teste ou CI no repositório (`package.json`, `Makefile`, `pyproject.toml`, `.github/` não existem). Depois de qualquer alteração, rodar uma checagem manual equivalente a:

- Contadores: `101` projetos totais e `33` certificações - `1130h` no cabeçalho (`README.md:32`) e no currículo; `44` catalogados é a soma dos contadores das 15 abas de projetos (o cabeçalho não mostra mais esse número desde `a842531`).
- Linhas por aba: cada uma das 15 abas de projetos tem exatamente o número de linhas numeradas que o `<summary>` declara (soma = 44).
- Uma linha por imagem: `33` linhas na tabela do README, `33` itens no currículo, `33` `.jpg` em `certification/`, `33` links únicos apontando para arquivos existentes.
- Horas: cada `<td>Hours</td>` e cada `<span class="period">` bate com o número no nome do arquivo; a ordem é decrescente por ano; as somas (653h, 477h, 1130h) batem.
- Nomes: o texto do link de cada linha do README é igual ao `data-en` correspondente do currículo (e, nas 5 certificações que já eram em inglês, igual ao texto PT do currículo); nenhuma linha em português sobra no README.
- Bilíngue: todo trecho de texto visível tem `data-en` (exceto nomes próprios, tecnologias, horas, anos, URLs e rótulos idênticos nos dois idiomas); `data-en` nunca vazio e nunca com `<` cru. Contar `data-en` antes e depois: o número só sobe se o texto novo foi traduzido. Rodar o bloco de "Como validar as duas versões".
- HTML balanceado nos dois arquivos (`html.parser`), `id`s de `<details>` únicos, `git diff --check` sem erros de whitespace.

## Fluxo de trabalho e commits

- **Uma ONG por linha:** os 9 itens da seção 4 (`ONGs-ongasis-site`, `ONGs-onfpd-site`, `ONGs-onfcq-site`, `ONGs-onggad-site`, `ONGs-ongbp-site`, `ONGs-ongab-site`, `ONGs-ongab-software`, `ONGs-ongbp-software`, `ONGs-onggad-software`) devem bater com a aba Social impact do README, na mesma ordem, com o mesmo `href` e o mesmo status (`✅` ↔ concluído, `❌` ↔ em andamento). Conferir os links com `curl -s -o /dev/null -w "%{http_code}" -L <url>`: `ongfpd` e `ongcq` foram typos e viraram `onfpd` e `onfcq` (os repositórios públicos são `ONGs-onfpd-templatesite` e `ONGs-onfcq-templatesite`).
- Um commit por assunto, sem misturar `docs`, imagens e conteúdo. Exemplo do trabalho de certificações: (1) imagens, (2) currículo, (3) `AGENTS.md`.
- Ao editar `index.html`, o diff tem que incluir **o texto novo em português e a tradução em `data-en`**. Se só um dos dois aparecer no diff, o trabalho está incompleto.
- O histórico do repositório usa mensagens `Up` (326 commits), o que não é descritivo. Usar mensagens curtas em pt-BR no formato `tipo: descrição`.
- **Mudança misturada no mesmo arquivo:** se o dono editou um arquivo que o agente já estava mexendo, os dois conjuntos de mudanças entram no mesmo `git diff`. Isolar com cópias em `/tmp/opencode`: salvar o estado final, reverter só as linhas do agente, commitar o ajuste do dono, restaurar o arquivo e commitar a parte do agente. Nunca `rebase`, `amend` ou `reset`. Ver "Separar mudanças misturadas sem reescrever histórico".
- **Commit no fim da tarefa, sempre** (pedido do dono). Antes: `git status`, `git diff`, `git log --oneline -10`; um assunto por commit; nunca commitar segredos ou `.env`.
- O `README.md` é Markdown com HTML bruto: funciona no GitHub, mas tags precisam ser balanceadas e `&` escapado (`&amp;`) no link de `The Git & Github Bootcamp`.

## Histórico do trabalho

### 2026-09-26 — análise de partida e diretrizes do agente

Sessão de reanálise do repositório antes de retomar o trabalho. Nada de conteúdo mudou: `git status` limpo, working tree sem alterações.

1. **Estado conferido:** 33 `.jpg` (18 em `2023/`, 15 em `2024/`), 33 linhas de certificação no README, 33 itens no currículo, `87` elementos com `data-en`, 17 abas `<details>`, soma dos contadores das 15 abas de projetos = 44. HTML do `index.html` balanceado (`html.parser` sem erros).
2. **Pendências confirmadas como ainda abertas:** o par `10-Docker-Project` (currículo) × `10-Docker-Simple-project` (README); o `<summary>` de Certifications do README com tags cruzadas (o dono pediu para manter); `id="Social impact"` com espaço.
3. **Ambiente:** `/tmp/opencode/` vazio (tmpfs) — validadores e `jsdom` da sessão anterior não existem mais e precisam ser recriados; node 24, npm 11, python3.14 disponíveis.
4. **Nova seção "Diretrizes do agente"** criada no topo do `AGENTS.md` (pedido do dono: "analise o projeto e defina suas diretrizes"). É o contrato operacional: papel, checagens antes de mexer, regras inegociáveis, fluxo da tarefa e obrigação de registrar ao encerrar. As seções detalhadas continuam sendo o fundamento; as diretrizes apontam para elas em vez de duplicar.
5. **Títulos das certificações em inglês no README** (pedido: "veja os nomes em inglês no site index.html e coloque em inglês aqui no readme"): 28 linhas da aba Certifications trocadas pelo texto do `data-en` do currículo, casadas pelo `href`. Conferido com script: 33 linhas, 1130h (653 + 477), nenhum link quebrado, nenhum nome divergente do currículo, `git diff` alterando só as linhas de certificação do `README.md`. Seções do `AGENTS.md` que diziam "títulos em português no README" foram atualizadas. Commits `6e65929` (README) e `fdd2756` (documentação).
6. **Nova regra de commit** (pedido: "sempre faça commit no final"): a regra antiga "não commitar sem pedido explícito" foi substituída — agora toda tarefa termina em commit, um assunto por vez. Registrada como conceito "Commit no fim de cada tarefa".

### 2026-09-25 — certificações e bilinguismo

Sessão em que as certificações viraram uma aba completa e o currículo ficou bilíngue. Cada linha é um bloco de trabalho, na ordem em que aconteceu.

1. **Pasta de imagens.** `certificarion/` foi renomeada para `certification/` (o nome do dono, com erro de grafação, foi mantido). As 33 imagens ficaram em `2023/` (18) e `2024/` (15).
2. **Nomes dos cursos.** Extraídos por OCR, não digitados: 33 títulos da Udemy, com correção manual de acentos. O procedimento está na seção de OCR.
3. **Aba Certifications no README** (commits `2065c8c`, `eaa9f9f`, `ef60365`, `1831f2a`, do próprio dono, mensagens `Up`): duas tabelas `Course | Hours | Year`, ordenadas da maior para a menor carga horária dentro de cada ano, com subtítulos `2023 - 18 certifications - 653h` e `2024 - 15 certifications - 477h`. Uma linha de total foi experimentada no topo e **removida a pedido do dono**: no README o total vive só no cabeçalho e no `<summary>`.
4. **Seção 5 do currículo** (commit `5ae6061`): 33 cursos, total `Total: 33 certificações - 1130h.` no topo, `id="certifications"` para permitir link direto. A mesma seção recebeu as mudanças de Stacks, a entrada Tech Leader e o reposicionamento de Formação/Idiomas que já estavam sem commit no working tree.
5. **Imagens versionadas** (commit `ccf436b`) e **`AGENTS.md`** documentado (commit `95c720b`).
6. **Seletor de idioma PT/EN** (commit `b9b203a`): 59 elementos traduzidos na primeira leva, `<title>` e `<meta description>` bilíngues, escolha salva em `localStorage["cv-lang"]`, e remoção do `(concluído).` dos 7 projetos prontos da seção 6.
7. **Títulos das certificações em inglês** (commit `b9b203a`): mais 28 `data-en`, chegando a 87 elementos traduzidos. Os 5 títulos que já estavam em inglês ficaram sem `data-en`.
8. **Análise das ONGs** (commit `83aff60`): os 9 itens da seção 4 foram comparados com a aba Social impact do README (mesma ordem, mesmo `href`, mesmo status). Confirmado com `curl` que `ongfpd` e `ongcq` davam 404; corrigidos para `onfpd` e `onfcq` na URL **e** no rótulo, no PT e no `data-en`, nos dois arquivos.
9. **Ajuste do dono no README** (commit `a842531`): imagem de capa comentada, `44 Catalogued Projects` removido do cabeçalho de contadores e `<summary>` de Certifications com o rótulo dentro de `<a href="#">`. O cabeçalho passou a ser `📁 Projects Overview - 101 | | 🎓 Certifications - 33 - 1130h | 📄 Currículo` — os **44 catalogados continuam valendo** como a soma dos contadores das 15 abas de projetos, só não aparecem mais no cabeçalho.
   - **Pendente de decisão:** nesse mesmo ajuste o `<summary>` ficou com as tags cruzadas (`<a>` fechando dentro do `<span>`), o que o `html.parser` acusa como HTML desbalanceado. O dono pediu para deixar como está; o validador continua reportando o problema. O conserto é fechar a tag na ordem: `<summary><a href="#">Certifications</a> <span ...>(33 certifications - 1130h)</span></summary>`.

## Pendências conhecidas (não corrigidas)

- `index.html` e `README.md` divergem no nome do projeto Docker (`10-Docker-Project` vs `10-Docker-Simple-project`).
- `README.md`: summaries com `href="#"`; `id="Social impact"` com espaço; cabeçalhos de tabela copiados (`Ebook-Project` em Social impact, `DevOps-Project` em Framework/Cybersecurity, `FrontEnd-Project` em GameDev); plurais `project` no singular; 27 imagens sem `alt`; bloco comentado `README.md:5-30` com números antigos.
- `index.html` sem `h1`, sem `<main>`, sem `meta description`, títulos de experiência em `<p class="title">` em vez de `h3`, ícones de link de 14×14 px.
- `101 projetos` não é derivável do repositório (API do GitHub retorna 42 repositórios públicos).
- Nomes dos arquivos com erro de grafação (`cerification-*`) foram mantidos de propósito, a pedido do dono do perfil; só o diretório foi corrigido (`certificarion` → `certification`).
