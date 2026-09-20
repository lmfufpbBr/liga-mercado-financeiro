# Blog da Liga de Mercado Financeiro UFPB

Site estático (Jekyll) para publicar a newsletter semanal, análises setoriais, perfis de membros e conteúdo institucional da Liga. Pensado para que **vários membros** consigam publicar sem depender de ninguém em especial — só precisa de uma conta no GitHub.

---

## 1. Colocar o site no ar (uma vez só)

O repositório já foi criado: **https://github.com/lmfufpbBr/liga-mercado-financeiro** (público, vazio). Falta só subir estes arquivos e ligar o Pages:

1. Extraia este zip numa pasta e, dentro dela, rode:
   ```bash
   git init
   git add .
   git commit -m "Site inicial da Liga de Mercado Financeiro UFPB"
   git branch -M main
   git remote add origin https://github.com/lmfufpbBr/liga-mercado-financeiro.git
   git push -u origin main
   ```
2. No repositório, vá em **Settings → Pages** e em "Build and deployment" escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`. Salve. (Se preferir, me avise depois de dar o push que eu configuro essa parte pelo navegador.)
3. Em 1–2 minutos o site estará no ar em `https://lmfufpbbr.github.io/liga-mercado-financeiro/` — os campos `url`/`baseurl` em `_config.yml` já estão configurados para esse endereço.
4. Se no futuro configurarem um domínio próprio, deixem `baseurl` vazio, ajustem `url` para o domínio e adicionem um arquivo `CNAME` na raiz.
5. Adicione os links reais da Liga em `_config.yml`, na chave `social:`.
6. Troque `assets/images/logo-touro.svg` pelo logo oficial da Liga (pode ser `.svg`, `.png` ou `.jpg` — só ajuste a referência em `_includes/header.html`).

Depois disso, qualquer alteração enviada para a branch `main` republica o site automaticamente — não precisa rodar nada manualmente.

## 2. Dar acesso a outros membros

Em **Settings → Collaborators** do repositório, adicione o usuário do GitHub de cada membro que vai publicar conteúdo. Cada um vai editar diretamente pelo site do GitHub (não precisa instalar nada) ou clonando o repositório, como preferir.

## 3. Como qualquer membro adiciona conteúdo (sem precisar de ninguém)

Cada tipo de conteúdo é um arquivo Markdown numa pasta. Existe um modelo pronto pra cada tipo em `_templates/`.

**Nova edição da newsletter:**
1. Copie `_templates/template-newsletter.md`.
2. Cole em `_newsletter/` com o nome `AAAA-MM-DD-titulo-curto.md` (ex.: `2026-09-21-destaques-da-semana-edicao-37.md`).
3. Preencha os campos do topo (`title`, `date`, `edicao`, `author`, `excerpt`) e o conteúdo abaixo.
4. Envie (commit) para a branch `main`. Pronto, já aparece no site.

**Nova análise setorial:**
1. Copie `_templates/template-analise.md` para `_analises/`, mesmo padrão de nome de arquivo.
2. Preencha e envie.

**Novo perfil de membro:**
1. Copie `_templates/template-membro.md` para `_membros/`, com o nome do arquivo sendo o nome da pessoa (ex.: `maria-silva.md`).
2. Preencha os campos e a bio. Adicione a foto em `assets/images/` (recomendo quadrada, ~400x400px) e aponte o campo `foto:` para ela.
3. Envie.

**Direto pelo GitHub, sem instalar nada:** dentro da pasta desejada (ex.: `_newsletter`), use o botão **Add file → Create new file**, cole o conteúdo do template, ajuste, e clique em **Commit changes**.

## 4. Ver como fica antes de publicar (opcional, para quem tem Ruby instalado)

```bash
bundle install
bundle exec jekyll serve
```

Abre em `http://localhost:4000/liga-mercado-financeiro/`.

## 5. Estrutura do projeto

```
_config.yml          → configurações do site (título, links, coleções)
_layouts/            → moldes de página (default, post, membro)
_includes/           → cabeçalho e rodapé
assets/css/style.scss → identidade visual (cores e fontes)
assets/images/       → logo, avatares
_newsletter/          → edições da newsletter (uma por arquivo)
_analises/            → análises setoriais (uma por arquivo)
_membros/             → perfis de membros (um por arquivo)
_templates/           → modelos em branco para copiar (não aparecem no site)
sobre.md              → página institucional "Sobre a Liga"
index.html            → página inicial
newsletter.html, analises.html, membros.html → páginas de listagem
```

## 6. O que ainda precisa de atenção

- A página `sobre.md` tem trechos marcados **[AJUSTAR]** com informações que só a Liga sabe (fundação, missão oficial, processo seletivo). Substituam antes de divulgar amplamente.
- O logo (`logo-touro.svg`) e o avatar padrão (`avatar-placeholder.svg`) são placeholders — troquem pelos arquivos reais.
- As edições de exemplo em `_newsletter/` e `_analises/` têm dados fictícios entre colchetes — sirvam só de modelo de formatação; apaguem ou substituam antes de publicar de verdade.
- Este README assume publicação via GitHub Pages nativo (sem build customizado). Se no futuro quiserem plugins que o GitHub Pages não suporta nativamente, dá pra migrar para GitHub Actions com poucos ajustes.
