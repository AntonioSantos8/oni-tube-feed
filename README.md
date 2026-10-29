# OniTube feed

Vídeos do OniTube (o "Shorts" do PC da loja no Daichi Market). O jogo baixa o `feed.json` e toca
cada vídeo por streaming, direto daqui — nada disso vai dentro do jogo.

- 40 vídeos verticais 540×960 (até 30 s), ~48 MB, com capa `.jpg` cada.
- Temas: `comida_jp`, `mukbang`, `slime`, `satisfying`, `viral` (uma pasta por tema = uma aba).
- Todos da Pexels, licença livre inclusive para uso comercial. Créditos em `CREDITOS.md`.

## Colocar no ar (GitHub Pages)

1. Crie um repositório **público** novo no GitHub, por exemplo `onitube-feed`.
2. Suba o conteúdo desta pasta (pode arrastar os arquivos na página do repositório, ou
   `git init` + `git push` aqui dentro).
3. No repositório: **Settings → Pages → Branch: `main` / pasta `/ (root)` → Save**.
4. Em um ou dois minutos o feed fica em `https://SEU-USUARIO.github.io/onitube-feed/feed.json`.
5. No Unity: **Japan Market → OniTube → Abrir configuração do feed** e cole esse link em *Feed Url*.

## Adicionar vídeos

Coloque o `.mp4` (vertical, de preferência 540×960) na pasta do tema, com o nome
`Título do vídeo @Autor.mp4` (e uma capa `Título do vídeo @Autor.jpg`, opcional). Depois rode no
Unity **Japan Market → OniTube → Montar feed.json de uma pasta**, escolhendo esta pasta, e suba de
novo. O jogo pega a lista nova sem precisar de build.

Para deixar um vídeo leve antes de subir:

```bash
ffmpeg -i entrada.mp4 -t 30 -vf "scale=540:960:force_original_aspect_ratio=increase,crop=540:960,fps=30" -c:v libx264 -preset slow -crf 27 -c:a aac -b:a 96k -movflags +faststart "Titulo @Autor.mp4"
```
