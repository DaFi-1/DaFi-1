# AGENTS.md

## Contexto do projeto

Repositório de perfil do GitHub **DaFi-1/DaFi-1**. Não contém código-fonte; é uma vitrine pessoal formada por dois arquivos e uma pasta de imagens:

- **`index.html`** — Currículo (estilo Lattes) do dono do perfil. Conteúdo em português (pt-BR), single-file com CSS inline e ícones SVG embutidos. Estrutura em seções numeradas (1. Contato → 9. Idiomas).
- **`README.md`** — Apresentação do perfil no GitHub (profile README), exibida na página principal do usuário. É o catálogo de projetos e habilidades, organizado em abas `<details>`/`<summary>` (Skills, Ebooks, Certifications, Social impact, Framework, Cybersecurity, DevOps, Backend, Systems, FrontEnd, GameDev, Deep Learning, Testing, NeoVim, Forks, Trash, Gaming-Diary).
- **`certification/`** — Imagens dos certificados, organizadas por ano em `certification/<ano>/cerification-<n>-<h>h-(<ano>).jpg`.

## Convenções

- Idioma dos arquivos: **português (pt-BR)**. Comentários/código em inglês quando técnico.
- Links de repositórios apontam para `github.com/DaFi-1/<repo>`.
- Projetos sem repositório publicado usam `https://github.com/DaFi-1` como destino (título "Em breve").
- Estado dos projetos: `✅` concluído | `❌` em desenvolvimento.
- Aba Certifications: uma linha por imagem, com colunas de curso (link para a imagem), horas e ano; o contador do `<summary>` deve bater com o total de imagens e a soma de horas (por ano e total) deve bater com a coluna `Hours`.
- `<details>`: cada aba precisa de `id` **único** e contagem de projetos consistente com o número de linhas da tabela.

## Regras

- Sempre manter os contadores do README (header, títulos das abas) consistentes entre si e com o que está listado.
- Manter `index.html` e `README.md` alinhados (ex.: número de certificações e projetos deve bater entre os dois arquivos).
- Alterações em `index.html` devem preservar HTML balanceado (todas as tags abertas foram fechadas) e incluir `<title>`.