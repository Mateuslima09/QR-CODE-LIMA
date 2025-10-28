 # Gerador de QR Code (qr-generator)

Link Site:https://mateuslima09.github.io/QR-CODE-LIMA/

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


