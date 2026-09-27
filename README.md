# Rodolfo Bastos — Personal Trainer

Site institucional + landing page de alta conversão do **Treino Fast RB**, criados para o personal trainer Rodolfo Bastos (Salvador/BA, [@rodolfobastos.rb](https://instagram.com/rodolfobastos.rb)).

## Páginas

- `index.html`: site institucional. Apresentação do Rodolfo, funcional na Praia do Flamengo, trail run nas dunas de Stella Maris, prova social e teaser do Treino Fast RB.
- `llms.txt`, `robots.txt`, `sitemap.xml`: SEO e leitura por buscadores/IA. Dados estruturados (JSON-LD) ficam no fim do `<head>` de cada página.
- `sobre.html`: história do Rodolfo (texto biográfico, slogan "vem pro meu mundo, papa" e vídeos). Feita a partir do texto enviado, para ser ampliada com mais dados.
- `treino-fast-rb.html`: landing page de vendas do **Treino Fast RB**. Treinos em casa, 20 min/dia, com os 3 níveis (Iniciante, Intermediário, Avançado) e o Método Completo, linkados direto para o checkout na Kiwify.
- `assets/`: logo (`logo.png`), favicon, apple-touch-icon, a imagem de compartilhamento social (`og-image.png`), a foto real do herói (`hero-portrait.jpg`), o vídeo de boas-vindas do Rodolfo na seção "Sobre" (`welcome.mp4`) e os vídeos reais da quadra (`quadra.mp4`), do funcional (`funcional.mp4`), das dunas (`dunas.mp4`) e do trail run (`trail-run.mp4`), cada um com seu poster (`*-poster.jpg`), usados pelas duas páginas.

As duas páginas são independentes (HTML/CSS/JS puro, sem build step) e estão linkadas entre si.

## Como visualizar localmente

As páginas carregam logo, fotos e vídeos por caminho relativo (`assets/...`). Abrir o arquivo direto pelo `file://` (duplo clique) costuma funcionar para as imagens, mas os vídeos (o de boas-vindas na seção "Sobre" e os da galeria: Quadra, Funcional, Dunas, Trail run) podem não carregar nesse modo — quanto maior o arquivo, mais chance de travar (o vídeo de boas-vindas e o das dunas, com ~10MB cada, são os mais sensíveis a isso). Para ver exatamente como fica publicado (e garantir que os vídeos carreguem), sirva a pasta com um servidor local simples, por exemplo:

```bash
python -m http.server 8000
```

e acesse `http://localhost:8000/index.html`. Não há dependências externas além das fontes do Google Fonts.

## Animações

Entradas ao rolar (`data-reveal`, escalonadas por grupo em um pequeno script no fim de cada página), revelação do título e da foto no herói, contador nos números, hover nas capas dos vídeos, FAQ com abertura suave e transição na troca de tema. Tudo em CSS e JavaScript puro. Quem tem "reduzir movimento" ativado no sistema (`prefers-reduced-motion`) vê tudo estático e sem nada escondido.

## Temas: escuro e claro (prévia para o Rodolfo escolher)

As duas páginas têm duas versões visuais. **Escuro**: preto com laranja. **Claro** (padrão): branco/creme com a paleta do Treino Fast RB (azul-marinho `#071b32`, amarelo `#fdce01`, azul `#0b6bcb`), com a logo em versão `assets/logo-light.png`.

Enquanto ele decide, há um seletor "Tema" fixo no canto inferior esquerdo (a escolha fica salva no navegador e vale para as duas páginas). Também dá para abrir direto por link: `?tema=claro` ou `?tema=escuro`.

Quando ele escolher, deixar só uma versão: remover o seletor (`.theme-switch` no HTML, CSS e o script "seletor de tema"), o script no `<head>` que lê `?tema=`, e o bloco de tokens do tema que não for usado (`html[data-theme="light"]` no claro; ou, se ficar o claro, mover seus valores para `:root` e apagar o escuro e `assets/logo.png`/`.logo-dark`).

## Publicar com GitHub Pages

1. Nas configurações do repositório, vá em **Settings → Pages**.
2. Em **Source**, selecione a branch `main` e a pasta `/ (root)`.
3. Salve. O site fica disponível em `https://<usuario>.github.io/<repositorio>/`.

## Pendências / próximos passos

- A galeria "Registros" ficou só com os 4 vídeos reais (Quadra, Dunas, Funcional, Trail run) por enquanto — os placeholders de ícone (Treino Fast RB, Comunidade, Praia do Flamengo, Rotina) foram removidos até que haja fotos/vídeos reais pra eles. O retrato do herói na home já usa uma foto real do Rodolfo, e a seção "Sobre" tem um vídeo de boas-vindas dele.
- Se novos vídeos/fotos chegarem depois, dá pra voltar a expandir a galeria seguindo o mesmo padrão dos tiles atuais (`.gal-tile-video` com poster + vídeo).
- Confirmar se serão adicionados mais depoimentos além dos dois já publicados na home e na landing page do Treino Fast RB.
- Domínio: `www.rodolfobastos.com.br` (arquivo `CNAME`, canonical e tags Open Graph já apontam para ele). O DNS é configurado no provedor do domínio, ver seção abaixo.

## Domínio próprio (www.rodolfobastos.com.br)

No provedor do domínio (ex.: Registro.br), criar:

- `www`: registro **CNAME** apontando para `joaoschaun33-cloud.github.io`
- domínio raiz (`rodolfobastos.com.br`, para redirecionar ao www): quatro registros **A** para `185.199.108.153`, `185.199.109.153`, `185.199.110.153` e `185.199.111.153`

Depois, em **Settings → Pages**, conferir o domínio `www.rodolfobastos.com.br` e marcar **Enforce HTTPS** quando o certificado for liberado (pode levar alguns minutos a horas).

## Contato

- WhatsApp: [+55 71 98850-9084](https://wa.me/5571988509084)
- Instagram: [@rodolfobastos.rb](https://instagram.com/rodolfobastos.rb)
