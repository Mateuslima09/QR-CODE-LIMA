# QR Generator (versão local)

Página estática para gerar múltiplos QR codes com opções visuais, tema e persistência local.

Última atualização: 29 de outubro de 2025

Link Site https://mateuslima09.github.io/QR-CODE-LIMA/

## Visão geral

Este projeto é um "single-file" (arquivo único) chamado `index.html` que contém a interface, estilos e scripts para gerar QR codes e personalizar a aparência da página. Ele usa a API pública de geração de QR (https://api.qrserver.com) para renderizar imagens QR no próprio navegador (mesma aba).

O objetivo desta versão foi adicionar usabilidade e recursos visuais sem necessidade de backend, tornando-o fácil de hospedar em um servidor estático (GitHub Pages, Netlify, etc.) ou abrir diretamente no navegador.

## Funcionalidades adicionadas

- Geração de QR na mesma aba (mesmo documento) — evita download automático e abre os resultados em uma seção de cartões.
- Contador de QR gerados com limite configurável (MAX_QR = 500).
- Botões Limpar (limpa os resultados gerados) e Reset (reinicia o contador, pede confirmação).
- Controle de espaçamento entre cartões (slider de espaçamento).
- Controle de tamanho do QR (campo e validação / clamp para evitar imagens gigantes).
- Tema claro/escuro (toggle no canto superior direito) com persistência em localStorage.
- Fundo animado por partículas em canvas com opção de ativar/desativar (persistido em localStorage).
- Painel de configurações (drawer) acessível via botão de engrenagem estilizado — opções: ligar/desligar partículas, escolher um dos 3 fundos visuais.
- Seletor de três fundos (gradiente roxo, nebulosa escura, azul acinzentado) com swatches e persistência.
- Seletor de idioma (Português BR / English) no drawer — toda a UI dinâmica suporta PT/EN e a preferência é persistida.
- Favicon embutido (data URL) para facilitar hospedagem sem assets externos.
- Acessibilidade: botão de engrenagem com `tabindex`, foco visível; drawer fecha com Esc; prefers-reduced-motion respeitado para animações.

## Uso

1. Abra `index.html` no navegador (duplo-clique ou arraste para a janela do browser) ou coloque a pasta em um host estático.
2. Insira o texto ou URL que deseja transformar em QR no campo principal.
3. Ajuste tamanho e espaçamento conforme desejar.
4. Clique em "Gerar" para ver os cartões com QR gerados abaixo.
5. Use "Limpar" para remover as imagens atuais. Use "Reset" para zerar o contador (há confirmação).
6. Abra o painel de configurações clicando na engrenagem (canto superior esquerdo) para alternar o fundo animado e trocar o background ou idioma.

## Persistência (localStorage)

As preferências e estados são salvos no armazenamento local do navegador:

- `qrCount` — contador de QR gerados
- `qr_theme` — tema: `light` ou `dark`
- `particles_enabled` — `true`/`false` para o fundo animado
- `bg_choice` — `bg-1` / `bg-2` / `bg-3` para o background selecionado
- `lang` — `pt` / `en` para idioma selecionado

Remoção: apagando os dados do site no DevTools -> Application -> Local Storage ou usando o botão Reset para o contador (não remove outras prefs).

## Arquivo relevante e constantes

- `index.html` — único arquivo do projeto.
- Constante `MAX_QR` é definida dentro do script no `index.html`. Para alterar o limite, edite esse valor diretamente.

Procure por `const MAX_QR =` no `index.html` para localizar e ajustar.

## Notas de desenvolvimento

- A animação de partículas roda em `<canvas id="bg-canvas">` e é controlada por uma API interna exposta como `window.particlesControl` com métodos `enable()` / `disable()` / `isEnabled()` — útil para testes programáticos.
- O drawer de configurações gerencia a visibilidade do botão de engrenagem para evitar sobreposição com o título.
- O CSS respeita `prefers-reduced-motion` para reduzir ou desativar animações para usuários que preferirem menos movimento.

## Testes rápidos (local)

1. Abra `index.html` em um navegador moderno (Chrome/Edge/Firefox).
2. Gere um QR simples (por exemplo, `https://example.com`) e verifique se a imagem aparece na seção de resultados.
3. Teste alternar tema, ativar/desativar partículas e trocar o background; recarregue a página para confirmar persistência.

## Problemas conhecidos / próximos passos

- Não há ícones SVG para as bandeiras (atualmente usa emoji). Podemos substituir por SVGs nítidos se preferir.
- Ainda falta implementar um degradê animado na borda do `.container` (pseudo-elemento `::before`) — planejado e listado no TODO.
- Validar performance em dispositivos móveis com partículas animadas ativas; considerar desativar por padrão em telas pequenas.

## Changelog (resumo)

- 2025-10-29: adicionadas as principais features descritas (drawer, partículas, tema, backgrounds, i18n, persistência, favicon, espaçamento, clear/reset, melhorias de acessibilidade e visual do botão de engrenagem).

## Hospedagem

Coloque o arquivo `index.html` (e quaisquer outros arquivos que desejar) em um diretório público e hospede em qualquer serviço de páginas estáticas (GitHub Pages, Netlify, Vercel, surge.sh, etc.). Não há dependências de backend.

## Créditos

- Gerador de QR utilizado: `api.qrserver.com` (serviço público de geração de QR via URL).

 # Gerador de QR Code (qr-generator)

Este projeto é um gerador simples de QR Codes que roda inteiramente no navegador. Cole uma lista de IDs (um por linha) e o site gera um QR code por ID, exibido em cartões numerados. Ele foi pensado para uso rápido sem servidor — ideal para imprimir ou baixar QR codes.

Funcionalidades principais
- Cole IDs (um por linha) e gere QR Codes em lote.
- Controle do tamanho do QR (px) e espaçamento vertical entre os cartões.
- Limpeza do campo de IDs e contador que registra quantos QR foram gerados (localStorage).
- Renderização em página única com botão "Voltar" para retornar ao formulário.

Como usar localmente
1. Abra `index.html` em um navegador moderno (Chrome, Edge, Firefox).
2. Cole os IDs no campo de texto (um por linha).
3. Ajuste "Tamanho do QR Code (px)" e "Espaçamento (px)" conforme desejar.
4. Clique em "Gerar QR Codes". Cada QR será exibido em um cartão numerado.
5. Para retornar ao formulário, clique em "Voltar". Use "Limpar IDs" para apagar o textarea.

Nota sobre o contador
- O contador de QR gerados é armazenado em `localStorage` no navegador (chave `qrCount`). Use o botão "Resetar Contador" para zerá-lo.

Limitações e comportamento
- O projeto usa um serviço externo (`api.qrserver.com`) para gerar as imagens dos QR Codes. Se preferir gerar QR totalmente offline, é possível integrar uma biblioteca JavaScript (ex: qrcodejs).
- O tamanho solicitado para o QR pode ser automaticamente reduzido para caber na tela — o site aplica um limite responsivo para evitar que a imagem "estoure" o cartão.


