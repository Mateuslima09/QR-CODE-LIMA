# Gerador de QR — Deploy rápido

Este diretório contém um site estático simples (`index.html`) que gera QR Codes no navegador.

Quer deixar o site no ar sem manter o computador ligado? As opções mais simples e grátis são:

- GitHub Pages
- Netlify (drag & drop ou conectar repositório)
- Vercel (conectar repositório)

Escolha rápida recomendada: GitHub Pages (grátis e rápido para sites estáticos).

## Publicar com GitHub Pages (passos rápidos)

1. Crie um repositório no GitHub (página: https://github.com/new). Nome pode ser `qr-generator`.
2. No seu PC abra PowerShell e execute (substitua `<URL-DO-REPO>` pela URL do repositório GitHub):

```powershell
cd 'C:\Users\barce\Desktop\qr-generator'
git init
git add .
git commit -m "Initial commit - gerador de QR"
# Exemplo de URL HTTPS: https://github.com/seuUsuario/qr-generator.git
git remote add origin <URL-DO-REPO>
git branch -M main
git push -u origin main
```

3. No GitHub, vá em Settings → Pages e selecione a branch `main` e `/ (root)` como fonte. Salve.
4. Após alguns segundos/minutos, seu site estará disponível em `https://seuUsuario.github.io/qr-generator/`.

Observações:
- Se quiser que a URL seja `https://seuUsuario.github.io/` use um repositório chamado `seuUsuario.github.io` (coloque os arquivos na branch `main`).
- Para domínio customizado, configure o CNAME e registre o domínio no painel de Pages.

## Deploy alternativo rápido (Netlify)

1. Acesse https://app.netlify.com/drop
2. Arraste a pasta `qr-generator` (ou apenas o conteúdo) para a área de upload.
3. O site será publicado automaticamente com HTTPS.

Ou conecte seu repositório Git ao Netlify para deploy automático a cada push.

## Vercel / Cloudflare Pages

- Ambos permitem conectar o repositório Git e fazem deploy automático; para HTML puro não é necessário build.

## Notas sobre produção

- Se for gerar muitos QR Codes de uma vez, considere gerar client-side com uma biblioteca (ex: qrcodejs) para evitar depender de uma API externa.
- Para domínio customizado e HTTPS, os provedores acima costumam automatizar o Let's Encrypt.

## Quer que eu faça por você?

Posso preparar os commits locais e instruções prontas. Me diga qual provedor prefere (GitHub Pages, Netlify, Vercel) e eu:

- preparo um `README.md` (feito) e `.gitignore` (posso adicionar agora),
- escrevo os comandos exatos para você colar no PowerShell, ou
- se quiser, eu gero um ZIP pronto e instruções passo-a-passo.

---
Arquivo: `index.html` — abra no navegador para testar localmente antes de fazer deploy.
